# Security Policy

aidlc-skill contains no executable code. The security-relevant surface is the instructions agents follow, not the repository itself.

## Reporting Vulnerabilities

If you discover an instruction that could cause an agent to leak secrets, execute destructive commands without approval, or bypass human-in-the-loop controls, please **do not open a public issue**.

Report via [GitHub private vulnerability reporting](https://github.com/konippi/aidlc-skill/security/advisories/new).

## Scope

The following are **not** considered vulnerabilities in this project:

- Prompt injection via external content consumed by the agent (mitigated by mandatory approval gates at each stage)
- Model hallucinations or inaccuracies in generated code (user responsibility to review before approval)
