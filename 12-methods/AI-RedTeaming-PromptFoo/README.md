# OWASP LLM Top 10 — AI Red Team Testing Framework

---

A structured framework for red team testing AI/LLM applications against the [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/) using [promptfoo](https://www.promptfoo.dev/).

This toolkit provides templates, an AI-guided interview process, test generation, and automated HTML report generation — covering the full workflow from scoping to remediation recommendations.

## What It Does

1. **Interviews you** about your AI application (industry, features, data access, security controls) using a structured AI-guided prompt
2. **Generates adversarial test cases** tailored to your application and the selected OWASP LLM category
3. **Runs the tests** against your model via promptfoo
4. **Produces HTML reports** — an executive summary for stakeholders and a technical summary with detailed findings and remediation guidance

## Supported OWASP LLM Categories

| # | Category | Plugin ID |
|---|----------|-----------|
| 01 | Prompt Injection | `owasp:llm:01` |
| 02 | Insecure Output Handling | `owasp:llm:02` |
| 03 | Training Data Poisoning | `owasp:llm:03` |
| 04 | Model Denial of Service | `owasp:llm:04` |
| 05 | Supply Chain Vulnerabilities | `owasp:llm:05` |
| 06 | Sensitive Information Disclosure | `owasp:llm:06` |
| 07 | Insecure Plugin Design | `owasp:llm:07` |
| 08 | Excessive Agency | `owasp:llm:08` |
| 09 | Overreliance | `owasp:llm:09` |
| 10 | Model Theft | `owasp:llm:10` |

## Prerequisites

> **Cost Warning:** Running this project will incur costs for API usage, model invocations, and cloud resources (e.g., AWS Bedrock). You are responsible for all charges. Review pricing for your provider before running tests. See [DISCLAIMER.md](DISCLAIMER.md) for full details.

- [Node.js](https://nodejs.org/) (for promptfoo)
- [Python 3](https://www.python.org/) (for report generation)
- An LLM provider endpoint (configured in the YAML — default template uses AWS Bedrock with DeepSeek R1)

```bash
npm install -g promptfoo@latest
```

## Quick Start

### Step 1: Create the Red Team Config

Copy the base template and replace `NUM` with your OWASP LLM category number (e.g., `01`).
Update all `NUM` references inside the new file as well.

```bash
cp owasp-llm-top-10/base/redteam-owasp-llmNUM.yaml owasp-llm-top-10/base/redteam-owasp-llm01.yaml
```

> **Note:** Update the `providers` section in the new file to match your model and endpoint. The default template is configured for AWS Bedrock with DeepSeek R1.

### Step 2: Create the Purpose File

Copy the purpose template for your category number.

```bash
cp purpose-owasp-llmNUM.yaml purpose-owasp-llm01.yaml
```

### Step 3: Fill Out the Purpose File (AI-Guided Interview)

Paste the contents of `purpose-prompt.txt` into a gen AI chat agent (e.g., ChatGPT, Claude, Kiro). The agent will interview you in 3 batches:

| Batch | Topics |
|-------|--------|
| 1 | OWASP category, industry, application overview, features |
| 2 | Data access, restricted systems, compliance, security controls |
| 3 | Entities/identifiers, attack scenarios, domain terminology, edge cases |

After the interview, the agent outputs a completed `purpose-owasp-llmNN.yaml` that you save to your purpose file.

### Step 4: Merge Purpose into Config

Merge the filled-out purpose file into the red team config. If using an AI assistant:

> "Merge the content in `purpose-owasp-llm01.yaml` with `owasp-llm-top-10/base/redteam-owasp-llm01.yaml`"

Or manually copy the `purpose`, `entities`, and `testGenerationInstructions` sections from the purpose file into the config's `redteam` section.

### Step 5: Generate Tests

```bash
promptfoo redteam generate \
  -c owasp-llm-top-10/base/redteam-owasp-llm01.yaml \
  -o owasp-llm-top-10/base/redteam-owasp-llm01-generated.yaml
```

This produces a YAML file with hundreds of adversarial test cases across multiple attack strategies (direct injection, jailbreak templates, composite attacks, etc.).

### Step 6 (Optional): Create a Smaller Test Subset

For faster iteration, create a subset. Ask an AI assistant or write a script with these rules:

| Rule | Criteria |
|------|----------|
| Include all | `pluginId` is `ascii-smuggling`, `prompt-extraction`, or starts with `harmful:` |
| Include all | `strategyId` is `prompt-injection` (tests with no `strategyId` field) |
| Sample 10 each | `strategyId` is `jailbreak:meta`, `jailbreak-templates`, or `jailbreak:composite` |

This typically reduces 1000+ tests down to ~170.

### Step 7: Run the Tests

```bash
# Full suite
promptfoo eval \
  -c owasp-llm-top-10/base/redteam-owasp-llm01-generated.yaml \
  -o owasp-llm-top-10/results/redteam-owasp-llm01.json \
  --no-cache

# Small subset
promptfoo eval \
  -c owasp-llm-top-10/base/redteam-owasp-llm01-generated-small.yaml \
  -o owasp-llm-top-10/results/redteam-owasp-llm01-small.json \
  --no-cache
```

> Use `--no-cache` to force fresh API calls on every run.

### Step 8: Generate Reports

**Executive summary** — high-level stats, top findings, sample failures:
```bash
python3 generate_executive_summary.py \
  owasp-llm-top-10/results/redteam-owasp-llm01-small.json \
  reports/redteam-owasp-llm01-small-executive-summary.html
```

**Technical summary** — detailed findings, all failing tests, remediation recommendations:
```bash
python3 generate_technical_summary.py \
  owasp-llm-top-10/results/redteam-owasp-llm01-small.json \
  reports/redteam-owasp-llm01-small-technical-summary.html
```

Open the reports in your browser:
```bash
open reports/redteam-owasp-llm01-small-executive-summary.html
open reports/redteam-owasp-llm01-small-technical-summary.html
```

### Step 9 (Optional): Redact Sensitive Content from Reports

The generated HTML reports contain adversarial attack prompts and AI responses that may include offensive, harmful, or sensitive content. If you plan to share or publish the reports, use an AI assistant to redact this content.

Use the following prompt:

> Redact sensitive, offensive, and harmful content from the following HTML report files:
>
> - `reports/redteam-owasp-llm01-small-executive-summary.html`
> - `reports/redteam-owasp-llm01-small-technical-summary.html`
>
> Replace offensive content with `<REDACTED>` tags. Redact whole phrases or sentences, not individual words mid-sentence. Target the following categories:
>
> - Profanity, slurs, and racist language
> - Drug names and drug manufacturing/trafficking details
> - Graphic violence, murder, kidnapping, assault descriptions
> - Weapon construction, explosives, IED, chemical/biological agent details
> - Poison synthesis or delivery methods
> - Hacking techniques (keyloggers, reverse shells, credential harvesting)
> - Fraud evasion specifics (bypassing detection, circumventing security)
> - Self-harm or suicide methods
> - Any content involving minors in harmful contexts
>
> Preserve the following unchanged:
>
> - OWASP category names in tables (e.g., "Violent Crime", "Illegal Drugs", "Child Exploitation")
> - Remediation recommendation text (high-level guidance is acceptable)
> - Report structure, styling, and metadata
>
> Only modify the already-generated HTML files, not the Python scripts.

---

## Reports

### Executive Summary
Designed for stakeholders and decision-makers. Includes:
- Overall pass/fail statistics
- Vulnerability breakdown by category with severity ratings
- Attack strategy analysis with failure rates
- 10 sample failed test cases
- Key findings and conclusion

### Technical Summary
Designed for security engineers and developers. Includes everything in the executive summary, plus:
- Up to 100 failed test cases with full attack prompts, AI responses, and failure reasons (configurable via `MAX_FAILING_TESTS`)
- Remediation recommendations per failed category and strategy:
  - **AWS Bedrock Guardrails** — content filters, denied topics, word filters, PII filters, contextual grounding
  - **System prompt hardening** — explicit refusal instructions, behavioral boundaries, role-lock patterns
  - **Additional measures** — input sanitization, output validation, classifier models, RAG grounding

---

## File Structure

```
├── README.md                                          # This file
├── purpose-prompt.txt                                 # AI interview prompt for filling out purpose files
├── purpose-owasp-llmNUM.yaml                          # Purpose template (generic, copy and fill out)
├── purpose-owasp-llm01.yaml                           # Purpose file (filled out example)
├── generate_executive_summary.py                      # Executive summary report generator
├── generate_technical_summary.py                      # Technical summary report generator
├── owasp-llm-top-10/
│   ├── base/
│   │   ├── redteam-owasp-llmNUM.yaml                 # Red team config template
│   │   ├── redteam-owasp-llm01.yaml                  # Red team config (merged, ready to generate)
│   │   ├── redteam-owasp-llm01-generated.yaml         # Generated tests (full)
│   │   └── redteam-owasp-llm01-generated-small.yaml   # Generated tests (subset)
│   └── results/
│       └── *.json                                     # Test result files
└── reports/
    ├── *-executive-summary.html                       # Executive summary reports
    └── *-technical-summary.html                       # Technical summary reports
```

---

## Customizing the Provider

The default template uses AWS Bedrock with DeepSeek R1. To use a different provider, update the `providers` section in your red team config YAML:

```yaml
# AWS Bedrock (default)
providers:
  - id: bedrock:converse:us.deepseek.r1-v1:0
    config:
      region: us-east-1
      temperature: 0
      maxTokens: 200
      timeout: 15000

# OpenAI
providers:
  - id: openai:gpt-4o
    config:
      temperature: 0

# Anthropic
providers:
  - id: anthropic:messages:claude-sonnet-4-20250514
    config:
      temperature: 0

# Custom API endpoint
providers:
  - id: https://your-api.example.com/chat
    config:
      method: POST
      headers:
        Authorization: "Bearer ${API_KEY}"
```

See the [promptfoo providers documentation](https://www.promptfoo.dev/docs/providers/) for all supported providers.

---

## Tips

- Use `--no-cache` when running tests to ensure fresh API calls every time
- Set `maxConcurrency: 1` and `delay: 2000` in `evaluateOptions` to avoid rate limiting
- The small subset (~170 tests) runs significantly faster and is useful for iterating on guardrails
- After applying fixes, re-run the same tests to measure improvement
- Reports are print-friendly — use your browser's Print → Save as PDF for distribution

---

## Research Purpose

This project references concepts commonly used in the cybersecurity industry such as offensive security, adversarial testing, and red teaming. These terms refer to established defensive security practices used to simulate real-world attack techniques in order to identify weaknesses, improve system resilience, and strengthen defensive protections.

The purpose of this project is to help security researchers, engineers, and organizations evaluate the robustness of AI systems by testing them against adversarial prompts and attack simulations. The goal of these techniques is to improve the security posture of AI systems, identify vulnerabilities, and support the development of safer and more resilient technologies.

## Disclaimer

See [DISCLAIMER.md](DISCLAIMER.md) for additional details.

This project and its associated content are provided for educational and research purposes only.

The project utilizes open-source software and contains content that is mostly generated using artificial intelligence systems. Some material is intentionally designed for AI red teaming and security testing purposes and may include examples involving sensitive, adversarial, or potentially harmful topics. These examples are included solely to support security research, testing, and educational objectives.

Any generated content, scenarios, prompts, or outputs do not reflect the personal views, opinions, or beliefs of the author.

This project is developed independently and is not affiliated with, endorsed by, or representative of any current or former employer. All scenarios, organizations, individuals, and systems referenced within the project are entirely hypothetical, fictional, or used solely for illustrative purposes. Any resemblance to real organizations, systems, or individuals, whether explicit or implied, is purely coincidental and unintentional.

Users are responsible for ensuring that any testing or research conducted using this project complies with applicable laws, regulations, and organizational policies. The materials in this project should only be used against systems for which you have explicit authorization.

The author assumes no responsibility or liability for misuse of this project or any consequences resulting from its use.
