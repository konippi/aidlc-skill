# aidlc-skill

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-green)](https://agentskills.io)

AI-Driven Development Life Cycle (AI-DLC) as an [Agent Skill](https://agentskills.io/) for any compatible coding agent.

## What is AI-DLC

> AI-DLC is an AI-centric transformative approach to software development that emphasizes two powerful dimensions:
>
> - **AI Powered Execution with Human Oversight**: AI systematically creates detailed work plans, actively seeks clarification, and defers critical decisions to humans.
> - **Dynamic Team Collaboration**: AI handles routine tasks so teams can focus on problem solving, creative thinking, and rapid decision-making.

Learn more: the [AI-DLC blog post](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) and the [Method Definition Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/).

## Install

```bash
npx skills add konippi/aidlc-skill
```

Or manually (pick the path your agent uses):

```bash
git clone https://github.com/konippi/aidlc-skill.git
ln -s /path/to/aidlc-skill ~/.claude/skills/aidlc-skill
ln -s /path/to/aidlc-skill ~/.kiro/skills/aidlc-skill
ln -s /path/to/aidlc-skill ~/.agents/skills/aidlc-skill
```

For project-scoped installation, symlink into `.claude/skills/`, `.kiro/skills/`, or `.agents/skills/` in your project root instead.

> [!NOTE]
> **Kiro CLI users**: After installing skills, add them to your custom agent's `resources` in `.kiro/agents/<agent>.json`:
>
> ```json
> {
>   "resources": ["skill://.kiro/skills/**/SKILL.md"]
> }
> ```

## Usage

Start any software development request with:

```text
Using AI-DLC, build a REST API for user management
```

The agent displays a welcome message, detects whether the workspace is greenfield or brownfield, and walks through the three-phase adaptive workflow with explicit approval gates between stages.

## Three-phase lifecycle

| Phase              | Purpose                                  | Key stages                                                                                               |
| ------------------ | ---------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Inception**      | What to build and why                    | Workspace Detection, Reverse Engineering, Requirements Analysis, User Stories, Workflow Planning, Application Design, Units Generation |
| **Construction**   | How to build it (per-unit loop + tests)   | Functional Design, NFR Requirements, NFR Design, Infrastructure Design, Code Generation, Build and Test   |
| **Operations**     | Placeholder for future deploy/monitor     | Operations (placeholder)                                                                                 |

See [`SKILL.md`](SKILL.md) for the exact activation contract, or open any [`references/<phase>/<stage>.md`](references/) for stage-level detail.

## Generated artifacts layout

Workflow output lands in `aidlc-docs/` in your workspace. Application code lands in the workspace root — never in `aidlc-docs/`:

```text
<workspace>/
├── [your application code]
└── aidlc-docs/
    ├── aidlc-state.md
    ├── audit.md
    ├── inception/
    ├── construction/{unit}/
    └── operations/
```

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md).

## Security

See [SECURITY.md](SECURITY.md) for reporting vulnerabilities.

## License

[MIT](LICENSE)
