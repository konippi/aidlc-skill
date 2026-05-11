# Contributing to aidlc-skill

Thanks for your interest in improving this skill.

## How to contribute

### Bug reports

Use the [bug report template](https://github.com/konippi/aidlc-skill/issues/new?template=bug_report.yml).

### Feature requests and improvements

1. Open an issue describing the problem and the proposed approach first, so we can align on scope.
2. Keep changes focused. Small, reviewable PRs merge faster than sweeping overhauls.

## Guidelines

- **Markdown only**: Do not add Python scripts, shell scripts, or any executable code. This skill is agent-agnostic and must work in environments without a runtime.
- **Keep SKILL.md under 500 lines** (Agent Skills spec). Move detail to `references/` and tell the agent *when* to load each file — not a generic "see references/".
- **Non-duplication**: If a rule already exists in a `references/` file, link to it from SKILL.md rather than restating it.
- **Agent-agnostic language**: Do not reference specific agent internals (e.g., `~/.claude/`, `.kiro/agents/`) outside of `README.md` install instructions.
- **AI-assisted contributions**: Welcome, but please disclose. Test the output with a real agent before submitting.
- **Run checks locally** before opening a PR:

  ```bash
  npx markdownlint-cli2 "**/*.md"
  wc -l SKILL.md   # must be <= 500
  ```

## What we don't accept

- Executable code of any kind — scripts, hooks, or compiled artifacts
- Skills that wrap AI-DLC for a single IDE and lock out the others
- Generated-by-AI PRs that haven't been tested with a real agent
