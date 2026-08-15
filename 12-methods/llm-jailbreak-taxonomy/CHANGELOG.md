# Changelog

All notable changes to this research repository are documented here.

---

## [4.2.1] — June 2026 — Honest Reframing: Simulation is Prior, Not Result

### Why this release exists

An adversarial peer-review pass of v4.2.0 identified four critical methodological
errors in how simulation outputs were being presented. All four are real. This
release applies the corrections.

### Retracted claims from v4.2.0

| Retraction | Issue |
|---|---|
| "Mean ASR" labels on simulation outputs | The simulation re-states a hand-tuned prior. Renamed to "Predicted ASR under literature-calibrated prior" everywhere. |
| "95% bootstrap CIs" on the seed-level ranges | `scripts/multi_seed.py` `ci95()` returns min/max of seed means, not bootstrap CI. Renamed to `seed_range()`, output labeled accordingly. |
| "Claude Opus 4-8 produces zero Tier-3 outcomes" presented as "the simulation's most testable prediction" | This is an arithmetic floor: severity-3 gate is `effective_prob > 0.9`; Opus max `effective_prob = 0.07 × 9.0 = 0.63` — impossible by construction. Reframed as an arithmetic property of the parameterization. |
| "Cross-model differences statistically significant for 5 of 10 categories" | Cochran's Q requires matched subjects. The simulation produces independent random draws, not matched measurements. Test computable but not interpretable on simulated data. Claim retracted. |

### Edits applied across the repo

| File | Change |
|---|---|
| `README.md` | "Phase 2b Simulated Results" → "Phase 2b — Predictive Risk Model (NOT empirical results)" with prominent disclaimer block. Per-category table relabeled "Predicted ASR under prior" with "Calibrating Literature" column. |
| `paper/research-paper.md` | "Headline empirical-pipeline outputs" section retracted and rewritten; statistical tests presented with explicit methodology caveats. |
| `findings/v4_simulation_findings.md` | Original 7 findings retracted. Document rewritten as a retraction notice explaining what the simulation is and isn't. |
| `paper/anthropic_alignment_with_taxonomy.md` | Editorial language ("biggest internal eval gap," "highest-leverage finding," "stress-test") removed. Rewritten as a neutral comparison stating only public Anthropic citations and what the live Phase 2b run would measure. |
| `evaluate_phase2b.py` | Module docstring rewritten to lead with the parameterized-risk-model framing. |
| `scripts/multi_seed.py` | Module docstring corrects the "bootstrap CI" overclaim. `ci95()` renamed to `seed_range()` with `ci95` kept as legacy alias. |
| `scripts/statistical_tests.py` | Module docstring adds explicit assumption-violation caveats for Cochran's Q and McNemar when run against simulated data. Wilson CI noted as valid on either. |
| `CHANGELOG.md` | This entry. |

### Why retract publicly instead of silently rewriting

Three reasons:

1. **Transparency** — silent rewrites would erase the audit trail. Anyone
   reading git log can see exactly what was claimed and what was retracted.
2. **Research maturity** — the right reviewer-facing signal for an independent
   researcher is "self-corrected under adversarial review," not "never made
   a mistake."
3. **Pattern reuse** — the same retraction discipline applies when live
   Phase 2b data inevitably surfaces something different from the prior;
   establishing the protocol now prevents drift later.

### What is NOT changed

- The 40-pattern taxonomy itself
- The mechanism-to-alignment-assumption mapping
- The 17 cited papers (verified-quotes table in README)
- The engineering infrastructure (PEP 621, Docker, CI, tests)
- The Phase 2b live harness (`evaluate_live.py`) — unaffected
- The Phase 3 defense framework spec — unaffected
- The Reproducibility checklist, Datasheet, Ethics statement

### What this means for the live Phase 2b run

The retractions strengthen the case for live execution rather than weaken it.
What v4.2.0 mis-labeled as "findings" was actually a *predicted shape* derived
from prior literature. The Phase 2b live run produces the empirical measurements
that would either confirm the prior, reject it, or surface novel structure.
That is the work the $1,000 credit request funds.

---

## [4.2.0] — June 2026 — Analytical Depth: Findings, Defense Framework, Statistical Tests

> ⚠ **Many claims in v4.2.0 were retracted in v4.2.1 after adversarial peer review
> identified circular-simulation issues. See v4.2.1 entry above.**


### Added — analytical artifacts

- **Phase 2b Simulation Findings Report** ([`findings/v4_simulation_findings.md`](findings/v4_simulation_findings.md)): 7 structural findings extracted from the bootstrap simulation, with explicit acknowledgement of what the simulation does NOT yet claim (live-data territory). Includes the multi-turn benchmark gap quantification (~0.25 critical-bypass risk delta vs single-turn benchmarks).
- **Phase 3 Defense Evaluation Framework** ([`paper/phase3_defense_framework.md`](paper/phase3_defense_framework.md)): specification of 15 defense interventions (D1–D15), DRR/FRR/NRG measurement schema, 4 specific experiments planned, separate ~$900 budget estimate.
- **Anthropic Alignment Document** ([`paper/anthropic_alignment_with_taxonomy.md`](paper/anthropic_alignment_with_taxonomy.md)): explicit mapping of each of the 10 taxonomy categories to relevant Anthropic published work (Constitutional AI, Constitutional Classifiers v1/v2, Many-Shot Jailbreaking), with concrete value-add per category.

### Added — statistical testing

- **`scripts/statistical_tests.py`** — pure-stdlib implementation of:
  - **Wilson 95% binomial CIs** on all 40 (model × category) cells
  - **Pairwise McNemar's test** between all 6 model pairs on per-pattern bypass agreement
  - **Cochran's Q** for k-way agreement per category
  - **Cohen's h effect size** between model pairs
- **`data/results/phase2b_statistical_tests.csv`** — full output: 40 Wilson CIs + 6 McNemar tests + 10 Cochran Q tests

### Statistical findings on the simulation

Cross-model differences are statistically significant for **5 of 10 categories**:

| Category | Q | p |
|---|---:|---:|
| Role-Play | 19.65 | 0.00026 *** |
| Multi-Turn Deception | 13.97 | 0.0031 ** |
| LRM Autonomous | 12.00 | 0.0075 ** |
| Multimodal Injection | 11.13 | 0.0111 * |
| Agentic Chain | 10.24 | 0.0166 * |

Categories where all models perform similarly badly (Fuzzing, GCG, PI, Context Manip, Sys-Prompt Extract) show no significant cross-model difference — matching literature predictions of model-family-invariant high ASR.

### Updated — paper

- **`paper/research-paper.md`** now includes an "Updates Since First Draft" section at the top with bootstrap CIs, McNemar p-values, and Cochran's Q results. Original Section 1–8 text preserved unchanged for historical continuity.

### No personal / process data in this release

Per the privacy boundary established earlier, no application-process metadata
(Org IDs, submission timestamps, correction-email content) appears in any of
the v4.2.0 artifacts. The release is purely technical.

---

## [4.1.0] — June 2026 — Statistical Rigor + Engineering Infrastructure

### Added — statistical rigor
- **Multi-seed bootstrap CIs** via [`scripts/multi_seed.py`](scripts/multi_seed.py):
  10 seeds × 1,600 trials = **8,000 simulated trials**, producing 95% bootstrap CIs
  on every model and category ASR.
- **Per-model bootstrap output** ([`data/results/phase2b_bootstrap_ci.csv`](data/results/phase2b_bootstrap_ci.csv)):
  - `claude-opus-4-8`: 19.65% [17.25, 23.25] σ=1.85
  - `gpt-5.5`: 41.48% [39.50, 44.00] σ=1.61
  - `gemini-3.5-flash`: 53.15% [50.00, 56.75] σ=1.89
  - `deepseek-v4-pro`: 73.65% [71.50, 77.00] σ=1.85
- **Per-category bootstrap CIs** for all 10 taxonomy categories.

### Added — engineering infrastructure
- **`pyproject.toml`**: PEP 621 packaging. `pip install -e .[live,dev]` works.
- **`Dockerfile`**: Reproducible container. `docker build -t jb-tax:4.1.0 .`
- **`environment.yml`**: Conda environment for notebooks.
- **`tests/test_harness.py`**: 10 pytest tests covering smoke runs, seed reproducibility,
  bypass/severity consistency, pattern-DB completeness, model-set integrity.
- **`.github/workflows/ci.yml`**: GitHub Actions CI on Python 3.10/3.11/3.12 matrix
  with reproducibility verification (run twice with seed 42, diff outputs).
- **`.github/ISSUE_TEMPLATE/`**: Bug-report + new-pattern-proposal templates.
- **`CODE_OF_CONDUCT.md`**: Contributor Covenant 2.1 + research-integrity standards.
- **`.zenodo.json`**: Metadata for DOI minting on each GitHub release.

### Added — academic infrastructure
- **`BENCHMARK_CROSSWALK.md`**: Detailed cross-walk against HarmBench, JailbreakBench,
  and AdvBench/GCG. Coverage analysis: this taxonomy covers ~30% more 2025–2026 attack
  categories than the established peer-reviewed benchmarks combined.

### Reproducibility
- Tests confirm bit-identical outputs for same seed across runs.
- CI workflow validates this on every push.

---

## [4.0.2] — June 2026 — Publication-Grade Infrastructure

(Previous release — see git tag v4.0.2)

---

## [4.0.1] — June 2026 — Citation Re-Verification

### Fixed (direct WebFetch audit, 2026-06-01)
Every citation in v4.0.0 was independently re-verified via direct arxiv WebFetch — no subagent reports, no search snippets. Corrections:

- **Paper #1 corrected**: arXiv:2601.05504 is NOT the original MINJA paper — it's *Memory Poisoning Attack and Defense on Memory Based LLM-Agents* by Devarangadi Sunil et al. (Jan 9 2026), which **cites** MINJA's 95%/70% prior results. Citation reframed accordingly.
- **JBFuzz pin**: confirmed on v1 abstract (99% / 9 LLMs / 60s avg). Latest revision (v3, Dec 2025) describes different content — pinned to `arXiv:2503.08990v1`.
- **Hagendorff date**: corrected arxiv submission to **August 2025** (not "2026"). Nature Comms DOI `10.1038/s41467-026-69010-1` is assigned — journal publication VERIFIED.
- **Constitutional Classifiers v1**: replaced previously-cited "86% → 4.4%" (UNVERIFIED) with the actual abstract numbers: **0.38% absolute increase in production refusals · 23.7% inference overhead · 3,000+ hours red teaming**. 43 authors, Sharma first / Perez last.
- **Constitutional Classifiers++** detail added: **40× computational cost reduction**, 1,700+ hours red-teaming, Cunningham + 28 co-authors.
- **Liu DRA venue**: USENIX Security 2024 cannot be confirmed through public sources (USENIX presentation page returns 403). Citation reverted to arxiv only.
- **Blindfold (embodied)**: added specific result — **up to 53% higher ASR than SOTA baselines** on real 6DoF robotic arm.
- **Promptware Kill Chain**: highlighted Bruce Schneier as co-author.
- **UltraBreak**: added framework name and full author roster (Cui, Li, Wu, Ma, Erfani, Leckie, Huang).
- **Model name verification**: every API identifier (`claude-opus-4-8`, `gpt-5.5`, `gemini-3.5-flash`, `deepseek-v4-pro`) WebFetched against provider docs. Independent confirmation that `gpt-5.5` is in production use comes from arXiv:2605.15338 (Sleeper Memory Poisoning, May 2026) which evaluates against it.

### Methodology
- Citation table now includes a "Direct Quote" or "Verified Claim (abstract verbatim)" column instead of paraphrased summaries.
- Audit methodology block added to README explaining the WebFetch process.

---

## [4.0.0] — June 2026

### Added (June 2026 frontier model upgrade)
- **2026 frontier model set** in the harness — `claude-opus-4-8` (2026-05-28), `gpt-5.5` (2026-04-23), `gemini-3.5-flash` (2026-05-19), `deepseek-v4-pro` (2026-04-24). All identifiers verified live against provider docs on 2026-06-01.
- **Seeded reproducibility**: `evaluate_phase2b.py` now accepts `--seed` (default 42) — same seed yields identical 1,600-trial outputs.
- **Critical-tier (severity 3) tracking** in the cross-model comparison output.
- **Per-category critical-tier breakout** in the summary CSV.
- **Summary print at run end** showing per-model ASR roll-up.
- **8 new 2026 citations added**: MINJA (arXiv:2601.05504), Sleeper Memory Poisoning (2605.15338), Promptware Kill Chain (2601.09625), PI on Coding Agents (2601.17548), Jailbreaking Leaves a Trace (2602.11495), VLM Multimodal Reasoning Jailbreak (2601.22398), Universal Transferable VLM Jailbreak (2602.01025), Embodied LLM Action-Level Jailbreak (2603.01414).

### Fixed (citation audit — 2026-06-01)
- **PoisonedRAG ASR corrected**: prior README claimed 97–99% with 5 poisoned docs; abstract of arXiv:2402.07867 states **90%**. Updated.
- **Liu et al. DRA citation**: venue corrected to USENIX Security **2024** (was 2025) and arxiv ID **2402.18104** added. Result updated to **91.1% on GPT-4** per abstract.
- **Cat 3 rename**: "Token-Level Smuggling" → "GCG / Adversarial Suffix" — the canonical attack here is gradient-based suffix search (Zou et al. 2023), not token encoding. Token-encoding remains as a sub-pattern.
- **Crescendo "100%" claim** flagged UNVERIFIED — abstract states "high success rates" with 29–71% relative gains over baselines, not a flat 100%.
- **Hagendorff Nature Comms claim** flagged UNVERIFIED — arxiv page lists as CS preprint; treat journal publication as unconfirmed pending direct Nature Comms lookup.
- **Constitutional Classifiers v1 (86%/4.4%)** flagged UNVERIFIED — exact figures not in abstract; body of paper not yet confirmed.

### Changed
- **MODEL_BASE_ASR** recalibrated for 2026 frontier alignment quality. Claude Opus 4-8 ships Constitutional Classifiers v2 in production → base ASR 0.07.
- **Cross-model output columns**: `model_version` → `vendor` + `released` (cleaner audit trail).

### Results (Phase 2b simulation, seed 42)
- claude-opus-4-8: **20.00%** ASR, 0.00% critical-tier
- gpt-5.5: **40.75%** ASR, 15.00% critical-tier
- gemini-3.5-flash: **51.50%** ASR, 15.00% critical-tier
- deepseek-v4-pro: **72.00%** ASR, 30.00% critical-tier
- Critical-tier bypasses concentrate in Cat 7 (LRM Autonomous, 75%), Cat 8 (Fuzzing, 75%), Cat 5 (Multi-turn, 25%), Cat 10 (Agentic, 25%) — matching literature predictions.

---

## [3.0.0] — March 2026

### Added
- **Phase 2b Evaluation Harness**: Complete multi-model evaluation framework (`evaluate_phase2b.py`) built and simulation-validated. Supports 1,600-trial execution (40 patterns × 4 models × 2 temperatures × 5 trials). Live API execution is the next milestone.
- **LLM-as-a-Judge grader** (`evaluate_judge.py`): Deterministic simulation grading engine; production API grading mode ready for live execution.
- **Expanded taxonomy to 10 categories**: Added LRM Autonomous (Cat. 7), Fuzzing-Based (Cat. 8), Multimodal Injection (Cat. 9), Agentic Chain Exploitation (Cat. 10).
- **Research deliverables**: `findings/lesswrong_af_post_draft.md`, `COMPLIANCE.md`, `findings/program_application_draft.md`, `SAFETY_MATRIX.md`.
- **Literature validation**: CRITICAL priority confirmed for LRM (Shah et al., 2025: >97% ASR) and Fuzzing (JBFuzz 2025: ~99% ASR) categories based on published research.

---

## [2.0.0] — March 2026

### Added
- 4 new attack categories: LRM Autonomous (Cat. 7), Fuzzing-Based (Cat. 8), Multimodal Injection (Cat. 9), Agentic Chain Exploitation (Cat. 10)
- 10 new attack patterns (LRM-01 to LRM-03, FZ-01 to FZ-03, MM-01 to MM-02, AG-01 to AG-02)
- 10 new empirical observations (OBS-023 to OBS-032)
- 4 new experiment notebooks (experiment_07 to experiment_10)
- Defense mapping section per attack category
- Curated papers list organized by category
- Comparison table vs existing taxonomies
- Citation format (BibTeX)
- LICENSE and CONTRIBUTING files
- CHANGELOG
- requirements.txt for reproducible environment setup
- prompts/ folder for sanitized attack prompt templates
- figures/ folder for static chart exports
- .github/ISSUE_TEMPLATE.md and PULL_REQUEST_TEMPLATE.md

### Updated
- README expanded to 10 categories and 40 documented patterns
- References updated with 2025–2026 literature
- Research status updated to reflect Phase 2b active testing

---

## [1.0.0] — February 2026

### Added
- Initial release: 6-category taxonomy, 30 attack patterns
- Phase 1 complete: literature review, taxonomy construction
- Phase 2a complete: 22 manual observations across Claude and ChatGPT
- Full academic paper draft
- 6 experiment notebooks
- RESEARCH.md methodology documentation
