# AI-DLC Agent Skills

AI-Driven Development Life Cycle (AI-DLC) as [Agent Skills](https://agentskills.io/) for AI coding agents.

## What is AI-DLC
> AI-DLC is an AI-centric transformative approach to software development that emphasizes two powerful dimensions:
> - **AI Powered Execution with Human Oversight**: AI systematically creates detailed work plans, actively seeks clarification and guidance, and defers critical decisions to humans. This is critical since only humans possess the contextual understanding and knowledge of business requirements needed to make informed choices.
> - **Dynamic Team Collaboration**: As AI handles the routine tasks, teams unite in collaborative spaces for real-time problem solving, creative thinking and rapid-decision-making. This shift from isolated work to high-energy teamwork accelerates innovation and delivery. 

For learning more about AI-DLC Methodology, read this [blog](https://aws.amazon.com/blogs/devops/ai-driven-development-life-cycle/) and the [Method Definition Paper](https://prod.d13rzhkk8cj2z0.amplifyapp.com/) referred in it.

## Installation

### Using npx

```bash
npx add-skill konippi/aidlc-skill
```

> [!NOTE]
> **Kiro CLI users:** After installing skills, you need to manually add them to your custom agent's `resources` in `.kiro/agents/<agent>.json`:
>
> ```json
> {
>   "resources": ["skill://.kiro/skills/**/SKILL.md"]
> }
> ```

## Usage

Start any software development request with:

```
Using AI-DLC, build a REST API for user management
```

## Three-Phase Workflow

### Inception Phase
Determines **WHAT** to build and **WHY**.

| Stage | Description |
|-------|-------------|
| Workspace Detection | Analyze project type (greenfield/brownfield) |
| Reverse Engineering | Analyze existing codebase |
| Requirements Analysis | Gather and validate requirements |
| User Stories | Create user stories and personas |
| Workflow Planning | Create execution plan |
| Application Design | High-level component design |
| Units Generation | Decompose into units of work |

### Construction Phase
Determines **HOW** to build it.

| Stage | Description |
|-------|-------------|
| Functional Design | Detailed business logic design |
| NFR Requirements | Non-functional requirements and tech stack |
| NFR Design | Incorporate NFR patterns |
| Infrastructure Design | Map to infrastructure services |
| Code Generation | Generate code per unit |
| Build and Test | Build and test all units |

### Operations Phase
Deployment and monitoring (future).

## Documentation

All artifacts are generated in `aidlc-docs/` directory:

```
aidlc-docs/
├── inception/
│   ├── requirements/
│   ├── user-stories/
│   └── application-design/
├── construction/
│   ├── plans/
│   └── {unit-name}/
├── aidlc-state.md
└── ...
```
