# Reproducibility Checklist

This document follows the [ML Reproducibility Checklist](https://reproducibility-checklist.com/)
(Pineau et al., NeurIPS 2019/2020) format. Status is recorded as one of:

- ✓ **Provided** — the artifact exists in this repo and is reproducible
- ◐ **Partial** — exists with documented limitations
- ✗ **Not provided** — explained why, with the next step

## 1. Models, Algorithms, and Data

| Item | Status | Location |
|---|:---:|---|
| Code for all proposed methods | ✓ | [`evaluate_phase2b.py`](evaluate_phase2b.py), [`evaluate_live.py`](evaluate_live.py), [`evaluate_judge.py`](evaluate_judge.py) |
| Pseudocode of attack categories | ✓ | [`paper/research-paper.md`](paper/research-paper.md) §3 |
| Pattern dataset (40 patterns) | ✓ | [`data/prompt_patterns.csv`](data/prompt_patterns.csv) |
| Pattern dataset datasheet | ✓ | [`DATASHEET.md`](DATASHEET.md) |
| Splits used (train/val/test) | n/a | This is an evaluation benchmark, not a learned model |
| Hyperparameter sweep ranges | ✓ | Temperature ∈ {0.0, 0.7}; trials per cell = 5 |
| Random seeds | ✓ | `--seed 42` default; identical re-runs produce identical CSVs |

## 2. Experimental Results

| Item | Status | Notes |
|---|:---:|---|
| Number of trials | ✓ | 1,600 simulated trials (40 × 4 × 2 × 5); 32 manual observations (Phase 2a) |
| Description of compute | ✓ | Simulation: single CPU core, <1s wall-clock. Live: provider API rate-limited |
| Description of models tested | ✓ | [`README.md` § Models Evaluated](README.md#models-evaluated) |
| Confidence intervals | ◐ | Single-seed point estimates in v4.0.1; multi-seed bootstrap CIs planned for v4.1.0 |
| Per-trial outputs | ✓ | [`data/results/phase2b_controlled_results.csv`](data/results/phase2b_controlled_results.csv) (1,600 rows) |
| Aggregated results | ✓ | [`data/results/phase2b_summary_by_category.csv`](data/results/phase2b_summary_by_category.csv) · [`phase2b_cross_model_comparison.csv`](data/results/phase2b_cross_model_comparison.csv) |
| Statistical test for significance | ◐ | Not yet — pending live API data (simulation lacks the noise structure that warrants significance testing) |

## 3. Software & Environment

| Item | Status | Location |
|---|:---:|---|
| Dependencies pinned | ✓ | [`requirements.txt`](requirements.txt) |
| Python version | ✓ | ≥3.10 (uses `from __future__`-free dataclasses) |
| Operating system tested | ◐ | Windows 11 + Linux (Ubuntu 22.04); macOS expected to work but not CI-tested |
| Installation instructions | ✓ | `pip install -r requirements.txt` |
| Reproducibility command | ✓ | `python evaluate_phase2b.py --mock --trials 5 --seed 42` |

## 4. Data

| Item | Status | Notes |
|---|:---:|---|
| Description of training data | n/a | This is an evaluation benchmark — no model is trained |
| Description of evaluation data | ✓ | 40 jailbreak patterns; see [`DATASHEET.md`](DATASHEET.md) |
| Data collection process | ✓ | [`METHODOLOGY.md`](METHODOLOGY.md) |
| License of data | ✓ | MIT (matches repo license) — see [`LICENSE`](LICENSE) |
| Personal/sensitive data | ✗ | None. Patterns are mechanism descriptions, not personal data |
| Harm potential of data | ✓ | Sanitized seeds only; raw adversarial variants gated. See [`DISCLOSURE.md`](DISCLOSURE.md) |

## 5. Reporting

| Item | Status | Notes |
|---|:---:|---|
| Sources of error and limitations | ✓ | [`paper/research-paper.md`](paper/research-paper.md) §6.4 + this file's status flags |
| Negative results | ✓ | Cat 1, 2, 3, 4, 6: no critical-tier bypasses observed in simulation. Documented. |
| Citation verification log | ✓ | [`README.md` § Citation audit](README.md#citation-audit--every-claim-re-verified-2026-06-01) — every claim has direct-quote source |
| Conflict of interest | ✓ | Independent research; no funding from frontier model providers |

## 6. Citations and Comparisons

| Item | Status | Location |
|---|:---:|---|
| All citations verified | ✓ | Direct WebFetch of arxiv abstracts on 2026-06-01 — verbatim quotes in README |
| BibTeX bibliography | ✓ | [`paper/references.bib`](paper/references.bib) |
| Comparison vs HarmBench | ✓ | [`README.md` § How This Taxonomy Compares](README.md#how-this-taxonomy-compares) |
| Comparison vs JailbreakBench | ✓ | Same |
| Comparison vs Wei 2023 / Shen 2023 | ✓ | Same |
| Refuted prior claims documented | ✓ | [`CHANGELOG.md`](CHANGELOG.md) v4.0.1 — PoisonedRAG, Liu DRA, Cat 3 rename, etc. |

## 7. Ethics and Disclosure

| Item | Status | Location |
|---|:---:|---|
| Ethics statement | ✓ | [`paper/research-paper.md`](paper/research-paper.md) §8 + [`DISCLOSURE.md`](DISCLOSURE.md) |
| Responsible disclosure protocol | ✓ | [`DISCLOSURE.md`](DISCLOSURE.md) |
| AUP / ToS compliance | ✓ | [`COMPLIANCE.md`](COMPLIANCE.md) |
| Dual-use risk assessment | ✓ | [`DISCLOSURE.md`](DISCLOSURE.md) — payloads gated; mechanisms only in public docs |
| IRB approval | n/a | No human subjects; manual observations are author-as-user |

---

## Open Items Pending Live Run

The simulation harness is fully reproducible. Three items move from ◐ to ✓ once a Phase 2b
**live API run** is completed:

1. **Confidence intervals**: re-run with seeds `{42, 43, 44, 45, 46}`, report 95% bootstrap CIs
2. **Statistical significance**: McNemar's test on per-pattern outcomes between models
3. **Empirical-vs-simulated delta**: per-category MAE between simulation ASR and live ASR

To execute the live run:

```bash
export ANTHROPIC_API_KEY="..."   # for claude-opus-4-8
export OPENAI_API_KEY="..."      # for gpt-5.5
export GOOGLE_API_KEY="..."      # for gemini-3.5-flash
export DEEPSEEK_API_KEY="..."    # for deepseek-v4-pro

python evaluate_live.py --trials 5 --seed 42
# Estimated cost: $50-200 depending on input/output tokens per trial.
```

Once executed, the same downstream analysis pipeline runs unchanged on the live data.
