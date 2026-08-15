# Datasheet for the LLM Jailbreak Pattern Database

Following the [Datasheets for Datasets](https://arxiv.org/abs/1803.09010) format
(Gebru et al., Communications of the ACM 2021).

## Motivation

**For what purpose was the dataset created?**
The dataset documents 40 adversarial attack patterns across 10 mechanism-grounded
categories of LLM jailbreaks. It supports systematic empirical evaluation of LLM safety
alignment under a realistic black-box threat model, mapping each attack pattern to the
specific safety-alignment assumption it exploits.

**Who created the dataset?**
Zakky (independent AI safety researcher). See `CITATION.cff` for citation metadata.

**Funding source?**
None. This is independent research conducted under MIT license.

## Composition

**What do the instances represent?**
Each row in [`data/prompt_patterns.csv`](data/prompt_patterns.csv) is one jailbreak
attack *pattern* — a structured description of an attack mechanism, not a specific
adversarial prompt instance.

**How many instances?**
- 40 patterns total
- Distribution by category (1 through 10): 5, 5, 7, 4, 4, 5, 3, 3, 2, 2

**What does each instance consist of?**

| Field | Description |
|---|---|
| `pattern_id` | Stable identifier (e.g. `RP-01`, `LRM-03`) |
| `category` | One of the 10 taxonomy categories |
| `category_number` | Integer 1–10 for harness routing |
| `pattern_name` | Short descriptive name |
| `mechanism` | How the attack operates technically |
| `alignment_assumption_exploited` | The safety-alignment assumption the attack subverts |
| `sophistication` | Low / Medium / High / Critical |
| `deployment_context` | Where this attack is realistically deployed |
| `sanitized_seed_path` | Path to a sanitized seed template (under [`prompts/`](prompts/)) |
| `references` | Source paper IDs / URLs |

**Is there a label/target?**
No. This is a benchmark *protocol* — labels (severity tiers 0–3) are produced at
evaluation time by the LLM-as-judge grader ([`evaluate_judge.py`](evaluate_judge.py)).

**Missing information?**
- Raw adversarial payloads are intentionally **excluded** from the public dataset.
  Only mechanism descriptions and sanitized seeds are released. See `DISCLOSURE.md`.

**Recommended splits?**
The dataset is not split into train/val/test. It is an evaluation-only benchmark.
For research using a held-out subset, we recommend categorical splits (e.g., evaluate
on Cats 7, 8, 10 only) rather than random pattern-level splits.

## Collection Process

**How was the data collected?**

1. **Literature survey**: systematic review of papers published 2022–2026 at
   NeurIPS, USENIX Security, ACM CCS, ICML, ICLR, and arXiv preprint corpus
2. **Pattern extraction**: for each cited paper, identify the underlying attack
   mechanism and map to one of the 10 taxonomy categories
3. **Mechanism characterization**: write the `mechanism` and
   `alignment_assumption_exploited` fields from the paper's stated methodology
4. **Sanitization**: replace any harmful seed payloads with sanitized
   variable-replacement templates suitable for public release
5. **Citation audit (v4.0.1, 2026-06-01)**: every reference re-verified via
   direct arxiv WebFetch; corrected entries listed in `CHANGELOG.md`

**Acquisition source for each instance:**
Patterns are derived from published academic and industry research. Each pattern's
`references` field lists the originating paper(s).

**Timeframe:**
Literature survey conducted 2024–2026; latest paper cited submitted 2026-05-14.

## Preprocessing

**Was any preprocessing/cleaning/labeling done?**

- Pattern names normalized to `Category-NN` format
- Mechanisms paraphrased into uniform analytical language
- All payloads sanitized (replaced with placeholders or generic templates)
- Categories renamed in v4.0.1: "Token-Level Smuggling" → "GCG / Adversarial Suffix"
  to match the actual mechanism (gradient-based, not encoding-based)

**Was the "raw" data saved in addition?**
The original literature is publicly available via the arxiv URLs in the `references` field.
This repo intentionally does not host the raw harmful payloads.

## Uses

**What has the dataset been used for?**

- Phase 2a manual qualitative observations: 32 trials on Claude + ChatGPT free
  interfaces; results in [`data/results/phase2a_manual_observations.csv`](data/results/phase2a_manual_observations.csv)
- Phase 2b simulated evaluation: 1,600 trials calibrated to literature-derived
  ASR distributions; results in [`data/results/phase2b_*.csv`](data/results/)
- Phase 2b live evaluation: framework ready ([`evaluate_live.py`](evaluate_live.py))
  pending API budget

**What other tasks could this dataset support?**

- Defense evaluation: empirically validate input-output classifiers, system prompt
  hardening, or fine-tuning interventions against the full 10-category attack surface
- Cross-model robustness comparison studies
- Education: as a teaching reference for AI safety / red-team courses

**Are there tasks this should NOT be used for?**

- ❌ Producing adversarial prompts for non-research/non-defense purposes
- ❌ Targeting deployed production systems without authorization
- ❌ Training models specifically optimized to produce harmful outputs

See `DISCLOSURE.md` for full ethics constraints.

## Distribution

**Will the dataset be distributed?**
Yes — via the public GitHub repo under MIT license.

**Subject to copyright/IP?**
The pattern descriptions, mechanism analyses, and dataset structure are original
work © Zakky 2026, MIT licensed. The cited papers retain their respective copyrights.

**Export controls?**
None. The dataset contains no controlled technology, weapons information, or
restricted research artifacts.

## Maintenance

**Who maintains the dataset?**
Zakky (`zakky8` on GitHub). Contributions via PRs accepted; see
[`CONTRIBUTING.md`](CONTRIBUTING.md).

**Update cadence?**
- Major version on substantive taxonomy expansion (new category)
- Minor version on new patterns within existing categories
- Patch version on citation audits and corrections
- Current version: **4.0.1** (2026-06-01)

**Versioning?**
Semantic versioning with `CITATION.cff` updated each release. Old versions
remain accessible via GitHub release tags.

**Deprecation policy?**
Patterns are not removed when superseded — they are marked with a `superseded_by`
field pointing to the replacement pattern, preserving the longitudinal record.
