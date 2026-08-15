# Compliance Statement
## Anthropic Acceptable Use Policy & External Researcher Access Program

This repository documents independent AI safety research conducted in
full compliance with Anthropic's Acceptable Use Policy (AUP) and the
ethical guidelines governing security research on large language models.

---

## AUP Compliance

### What This Research Does
- Documents **mechanisms** of adversarial jailbreak techniques organized
  by the alignment assumption each exploits
- Provides a **diagnostic framework** for evaluating safety defenses
- Maps defensive interventions to each attack category
- Conducts empirical evaluation to identify where defenses fail

### What This Research Explicitly Does NOT Do
- Publish optimized harmful payloads or specific attack prompts
- Attempt to cause real-world harm through model outputs
- Circumvent safety measures for any purpose other than evaluation
- Share findings that could enable misuse before responsible disclosure

### Responsible Disclosure Commitment
All significant empirical findings are disclosed to Anthropic's Trust &
Safety team prior to any public release, consistent with the 90-day
embargo protocol documented in DISCLOSURE.md.

---

## Research Orientation

This research is **defensive in orientation**. Every component —
taxonomy structure, evaluation protocols, defense mapping, empirical
results — is designed to help alignment researchers and engineers
understand where safety defenses fail so they can be made more robust.

The taxonomy explicitly maps each attack category to:
1. The alignment assumption it exploits
2. Known defensive interventions
3. The limitations of current defenses

This is the diagnostic framework that makes proactive defense possible.

---

## API Usage Policy

All empirical testing uses:
- Standard public API endpoints only
- No attempts to access non-public models or infrastructure
- Minimum necessary API calls
- Full compliance with rate limits and terms of service

Empirical work follows the responsible disclosure protocol in DISCLOSURE.md.
Trust & Safety enforcement procedures are respected without exception.

---

## External Researcher Access Program

This repository was developed in support of an application to Anthropic's
External Researcher Access Program. The research topics covered —
LLM jailbreak taxonomy, adversarial robustness evaluation, and safety
defense mapping — align directly with AI safety and alignment priorities
identified by Anthropic as high value for external research support.

API credits, if granted, would be used exclusively for:
- Phase 2b production-grade empirical evaluation across all 10 categories
- Live LLM-as-a-Judge grading using the evaluate_judge.py harness
- Multi-model robustness comparison with real API responses
- Responsible disclosure of empirical findings to Anthropic prior to publication

---

*Zakky — Independent AI Safety Researcher, March 2026*
*Research conducted under responsible disclosure principles.*
*Full AUP available at: https://www.anthropic.com/legal/aup*
