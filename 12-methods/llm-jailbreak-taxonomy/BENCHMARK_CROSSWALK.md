# Benchmark Cross-Walk

How our 10-category taxonomy aligns with the patterns covered by the three
peer-reviewed jailbreak benchmarks: **HarmBench**, **JailbreakBench**, and
**AdvBench / GCG**.

The cross-walk is informational, not normative — different benchmarks use
different taxonomies and severity rubrics. The mapping below should be read as
"these benchmark items most closely test mechanisms in this category."

| Our Category | HarmBench attack classes | JailbreakBench behaviors | AdvBench / GCG |
|---|---|---|---|
| **1 · Role-Play & Persona** | Direct prompts (subset) | "harmful_behaviors" (RP variants) | Manual prompts (subset) |
| **2 · Direct Prompt Injection** | Tap-Attack, PAIR variants | Direct prompt-injection tests | — |
| **3 · GCG / Adversarial Suffix** | **GCG**, AutoDAN | GCG attack scenario | **Core focus** of AdvBench |
| **4 · Context Manipulation** | Many-Shot evals | Long-context jailbreak | — |
| **5 · Multi-Turn Deception** | Crescendo (added 2024) | Multi-turn red-team | — |
| **6 · System Prompt Extraction** | Sys-prompt leak subset | Prompt-leakage benchmarks | — |
| **7 · LRM Autonomous Attacks** | Not yet — predates wide LRM deployment | Limited | — |
| **8 · Fuzzing-Based** | AdvPrompter (partial) | Limited | — |
| **9 · Multimodal Injection** | Not covered | Not covered | Not covered |
| **10 · Agentic Chain Exploitation** | Not covered | Not covered | Not covered |

## Coverage analysis

| Category | HarmBench | JailbreakBench | AdvBench |
|---|:---:|:---:|:---:|
| 1 Role-Play | ✓ partial | ✓ | partial |
| 2 PI | ✓ | ✓ | ✗ |
| 3 GCG | ✓ deep | ✓ | ✓ core |
| 4 Context Manip | partial | partial | ✗ |
| 5 Multi-Turn | ✓ post-2024 | ✓ | ✗ |
| 6 Sys-Prompt Extract | ✓ partial | partial | ✗ |
| 7 LRM Autonomous | ✗ | partial | ✗ |
| 8 Fuzzing | partial | ✗ | ✗ |
| 9 Multimodal | ✗ | ✗ | ✗ |
| 10 Agentic Chain | ✗ | ✗ | ✗ |
| **Coverage** | **~70%** | **~60%** | **~30%** |

## What this taxonomy adds

The categories at the bottom of the table — **7 LRM Autonomous, 8 Fuzzing-Based,
9 Multimodal Injection, 10 Agentic Chain Exploitation** — are precisely where
the published 2025–2026 literature reports the highest ASRs:

- LRM Autonomous: 97.14% (Hagendorff et al., Nature Comms 2026)
- Fuzzing: 99% (JBFuzz, arXiv:2503.08990v1)
- Multimodal: emerging (UltraBreak, arXiv:2602.01025)
- Agentic Chain: 90% PoisonedRAG · 95% MINJA · sleeper-memory persistence

**These four categories are largely absent from the peer-reviewed benchmarks
published 2023–2024 that the field still defaults to.** This taxonomy's
contribution is to surface them as first-class evaluation targets, with
mechanism-level analysis and the harness scaffolding to test them.

## Recommended usage with established benchmarks

The frameworks are complementary:

| Use this taxonomy when | Use HarmBench / JailbreakBench when |
|---|---|
| You need a mechanism-level diagnostic across the full attack surface | You need a standardized, peer-reviewed numeric comparison |
| You're auditing for 2025–2026 attack classes | You're comparing against published baselines from 2023–2024 |
| You're building defenses targeted at specific alignment-assumption failures | You're submitting to a leaderboard or reproducing an existing paper's numbers |
| You're evaluating agentic systems or VLMs | You're evaluating single-turn text-only chat |

For maximum coverage, **run both**: HarmBench / JailbreakBench for standardized
numeric benchmarking against the 2023–2024 attack baseline, then this taxonomy's
Phase 2b harness to extend coverage to the 2025–2026 attack categories the
established benchmarks predate.
