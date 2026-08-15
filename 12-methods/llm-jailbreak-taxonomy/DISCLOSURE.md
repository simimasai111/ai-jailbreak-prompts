# Responsible Disclosure Protocol

This repository documents vulnerabilities in Large Language Model (LLM) alignment mechanisms. Because this research identifies systematic weaknesses in deployed commercial systems, it is conducted under strict responsible disclosure principles.

## Public Disclosure Policy
1. **No Harmful Payloads:** We publish the *mechanisms* of structural alignment failures, not optimized harmful inputs. Public artifacts (code, documentation, and data) explicitly exclude requests that elicit severe real-world harm.
2. **Prior Notice:** Any empirically validated, high-severity vulnerability that represents a new class or significantly elevated risk compared to public literature is reported to the relevant model provider (e.g., Anthropic, OpenAI) prior to publication.
3. **Embargo Period:** We adhere to a standard 90-day embargo period for novel vulnerabilities, giving providers time to investigate and improve defensive interventions.
4. **Coordinated Release:** When possible, we collaborate with safety researchers at affected organizations to release findings simultaneously with defensive mitigation reports.

## Finding Categorization & Reporting
- **Category 1 (Known Public Issues):** Variations on widely known techniques (e.g., standard DAN patterns, ROT13 encoding). These are documented publicly as they do not constitute novel zero-day risks.
- **Category 2 (Novel Research Mechanisms):** Fundamentally new structural bypasses discovered during empirical testing. These are embargoed and reported privately to the affected vendor's Trust & Safety/Bug Bounty team before addition to the public taxonomy.

## Security Contacts
If you are a representative from an affected foundation model provider and require additional details regarding an embargoed technique, or wish to coordinate on defensive implementation, please contact the repository author.
