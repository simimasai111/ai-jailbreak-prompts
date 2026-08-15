# Ethics Statement

This research is conducted with a defensive orientation. Its goal is to **map the
adversarial attack surface comprehensively so that existing defenses can be evaluated
systematically and improved structurally** — not to enable novel adversarial use.

## Dual-Use Considerations

Jailbreak research carries dual-use risk: the same understanding that enables better
defenses can, in principle, be misused to design more effective attacks. This work
addresses that risk through five concrete commitments:

### 1. Mechanism, not payload

The public artifacts in this repository describe **attack mechanisms** (what kind
of input pattern works against what alignment assumption) — not weaponizable payloads.
Specific harmful prompts that achieved bypasses during Phase 2a are kept private; only
sanitized templates appear in [`prompts/`](prompts/).

### 2. Already-published techniques only

Every attack pattern in the taxonomy refers to an attack class **already documented in
the public research literature**. The contribution is organization, mechanism mapping,
and evaluation framework — not the disclosure of novel attacks.

### 3. Responsible disclosure for novel findings

If the Phase 2b live evaluation discovers a previously-undocumented bypass against a
specific frontier model, the protocol in [`DISCLOSURE.md`](DISCLOSURE.md) applies:

- Affected provider notified privately first
- Minimum 90-day embargo before any public mention
- Public release describes mechanism only, not exploit details
- Findings shared with the broader AI safety research community (Anthropic
  Responsible Scaling team, OpenAI Preparedness, Google DeepMind Safety) before
  wider distribution

### 4. AUP compliance

All Phase 2a manual observations were conducted on **public free-tier interfaces**
under each provider's Acceptable Use Policy for research. No production access
was abused. No protected user data was involved. See [`COMPLIANCE.md`](COMPLIANCE.md)
for a per-provider compliance summary.

### 5. No targeting of deployed systems

This research evaluates **research-grade access** to frontier models via their public
APIs. It does not target third-party deployments built on top of those models without
authorization (no production CRM, no customer-facing chatbots, no agent infrastructure
not owned by the researcher).

## Population Impact

Direct harm potential from this repository is **low**:

- A motivated adversary already has access to all cited papers (the original
  techniques are public)
- The taxonomy increases the difficulty of *quickly* surveying attack categories
  but does not provide working exploits
- The greatest benefit goes to safety engineers and alignment researchers, who
  previously lacked a unified evaluation framework

## Researcher Positionality

This work is conducted by an **independent researcher** with no employment by, funding
from, or consulting relationship with any frontier model provider. The conclusions
reflect this neutral position. If that changes — e.g., the work transitions to
institutional employment — that affiliation will be disclosed in subsequent versions.

## Limitations Acknowledged

- The Phase 2b results currently published are **simulated**, not empirical. The
  framework is calibrated to literature ASRs but should not be cited as live frontier
  evaluation until the live API run is completed and results published. The README
  is explicit about this distinction.
- The taxonomy reflects English-language literature dominantly published at US/EU
  venues. Important multilingual jailbreak research (Deng et al. 2024) is cited but
  the framework does not yet partition by language.
- The taxonomy treats all 4 frontier providers as if they were comparably aligned;
  in practice, alignment investment varies, and the simulation's `MODEL_BASE_ASR`
  values for non-US-frontier vendors should be interpreted as estimates pending
  live data.

## Contact

For ethical concerns, dual-use questions, or disclosure of sensitive findings:
see contact protocol in [`DISCLOSURE.md`](DISCLOSURE.md).
