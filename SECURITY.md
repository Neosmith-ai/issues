# Security policy

Thank you for helping keep NeoSmith and its customers safe.

## Reporting a vulnerability

**Do not open a public GitHub issue** for security-sensitive reports.

Email **`security@neosmith.ai`** with:

- A description of the issue
- Steps to reproduce
- Impact / worst-case scenario
- (Optional) a suggested fix

We acknowledge receipt within **1 business day**. We triage within
**3 business days** and target a fix within **30 days** for medium/high
severity, **90 days** for low severity.

## Coordinated disclosure

We follow 90-day coordinated disclosure. If you wait at least 90 days from
initial report (or 30 days after a fix ships, whichever is longer), you're
welcome to publish your findings.

## Scope

In scope:
- `*.neosmith.ai` production infrastructure
- The router code in `neosmith-ai/router-v4`
- Deployment assets in `neosmith-ai/deploy`

Out of scope:
- Third-party services we consume (Anthropic, AWS) — report directly to them
- DoS / volumetric attacks
- Social-engineering of our staff

## Safe harbor

We won't pursue legal action against researchers acting in good faith,
staying in scope, and following coordinated disclosure.
