---
name: aidlc-skill
description: "AI-DLC (AI-Driven Development Life Cycle) adaptive workflow for software development. Use when the user request starts with 'Using AI-DLC', or when a request spans multiple components, services, or user touchpoints and needs structured requirements, design, and per-unit implementation across Inception, Construction, and Operations phases. Do NOT use for simple bug fixes, single-file edits, documentation-only updates, or questions that do not require multi-stage planning."
license: MIT
metadata:
  author: konippi
---

# AI-DLC

An adaptive software development workflow. The workflow adapts to the work, not the other way around — the agent assesses user intent, existing codebase, complexity, and risk, then executes only the stages that add value.

## When to use

Activate this workflow when:

- The user request starts with `Using AI-DLC, ...`
- The request needs structured planning, requirements analysis, design, or per-unit code generation
- The request spans multiple components, services, or user touchpoints

When activated, this workflow **OVERRIDES** any other built-in software-development workflow.

## Path convention

The resolved rule-details directory for this skill is `references/`. All file paths below and inside the reference files (e.g. `common/process-overview.md`, `inception/workspace-detection.md`) are relative to `references/`.

## Workflow initialization (ONCE per workflow)

1. **Check for existing session** — If `aidlc-docs/aidlc-state.md` already exists with completed stages, this is a **session resume**. Compare the user's current request against the project described in the state file — if it is a different project, ask the user whether to archive the old state and start fresh or resume the existing project. If resuming, skip Steps 2-4, load `references/common/session-continuity.md`, and follow its resume protocol. Do NOT display welcome again or overwrite existing files.
2. **Display welcome** — Load and show `references/common/welcome-message.md`. Do this exactly once; do not reload it in later turns.
3. **Create state file** — Create `aidlc-docs/aidlc-state.md` using the scaffold in `references/common/state-template.md`.
4. **Create audit file** — Create `aidlc-docs/audit.md` using the scaffold in `references/common/audit-template.md`. Treat this file as append-only from now on (see Audit logging contract below).
5. **Load common rules** — MANDATORY. Load these four files and keep them in context for the whole workflow:
   - `references/common/process-overview.md`
   - `references/common/session-continuity.md`
   - `references/common/content-validation.md`
   - `references/common/question-format-guide.md`
6. **Scan extensions** — Read Extensions loading below. Load ONLY `*.opt-in.md` files at this point; do NOT load full rule files yet.
7. **Proceed to Workspace Detection** (first Inception stage).

## Stage Execution Protocol (applies to every stage)

Every stage in every phase follows this exact contract. Do NOT invent emergent variations.

1. **Log user input** in `aidlc-docs/audit.md` with complete raw input (see Audit logging contract).
2. **Load the stage's reference file** from `references/<phase>/<stage>.md` — that file contains the stage's full steps, question formats, and completion message.
3. **Execute** at the depth selected by Workflow Planning (minimal / standard / comprehensive — see `references/common/depth-levels.md`). For stages that run before Workflow Planning (Workspace Detection, Requirements Analysis), determine depth adaptively based on request complexity.
4. **Validate** every artifact before writing it using `references/common/content-validation.md`.
5. **Present the standardized completion message** defined in the stage's reference file. For Construction stages this is always a 2-option message (`Request Changes` / `Continue to Next Stage`) — never a 3+ option menu.
6. **Wait for explicit user approval** — do NOT proceed until the user confirms.
7. **Log user response** in `aidlc-docs/audit.md` with complete raw input.
8. **Mark the plan checkbox `[x]`** in the same turn the work completed (Plan-Level Checkbox Enforcement below).

## Inception phase — WHAT to build and WHY

Determine the problem shape and the execution plan. Workspace Detection, Requirements Analysis, and Workflow Planning always run; the rest are conditional and decided during Workflow Planning.

| Stage                   | Execution                          | Reference file                                |
| ----------------------- | ---------------------------------- | --------------------------------------------- |
| Workspace Detection     | ALWAYS                             | `references/inception/workspace-detection.md` |
| Reverse Engineering     | Brownfield only (no prior RE docs) | `references/inception/reverse-engineering.md` |
| Requirements Analysis   | ALWAYS (hosts extension opt-ins)   | `references/inception/requirements-analysis.md` |
| User Stories            | CONDITIONAL (see stage file)       | `references/inception/user-stories.md`        |
| Workflow Planning       | ALWAYS                             | `references/inception/workflow-planning.md`   |
| Application Design      | CONDITIONAL                        | `references/inception/application-design.md`  |
| Units Generation        | CONDITIONAL                        | `references/inception/units-generation.md`    |

**Stage-file triggers** — read the "Execute IF / Skip IF" block at the top of each stage file for the exact decision rules. Default bias: include a stage when in doubt.

## Construction phase — HOW to build it

For each unit produced by Units Generation, run the Per-Unit Loop to completion before starting the next unit. Build and Test runs once, after all units are done.

### Per-Unit Loop

| Stage                 | Execution               | Reference file                                     |
| --------------------- | ----------------------- | -------------------------------------------------- |
| Functional Design     | CONDITIONAL per-unit    | `references/construction/functional-design.md`     |
| NFR Requirements      | CONDITIONAL per-unit    | `references/construction/nfr-requirements.md`      |
| NFR Design            | CONDITIONAL per-unit    | `references/construction/nfr-design.md`            |
| Infrastructure Design | CONDITIONAL per-unit    | `references/construction/infrastructure-design.md` |
| Code Generation       | ALWAYS per-unit         | `references/construction/code-generation.md`       |

Code Generation is a two-part stage within one loop: Part 1 produces a plan with checkboxes and waits for approval; Part 2 executes the approved plan.

**Simple-path rule**: If Units Generation was skipped, treat the entire project as a single implicit unit. All per-unit conditional stages (Functional Design, NFR Requirements, NFR Design, Infrastructure Design) are also skipped — their prerequisite (units defined) is not met. Code Generation uses `requirements.md` directly — do not attempt to load non-existent unit design artifacts.

### After all units

| Stage          | Execution | Reference file                              |
| -------------- | --------- | ------------------------------------------- |
| Build and Test | ALWAYS    | `references/construction/build-and-test.md` |

## Operations phase — placeholder

Currently a placeholder. Build and test artifacts are produced in the Construction phase. See `references/operations/operations.md` for the forward-looking surface.

## Extensions (MANDATORY, context-optimized loading)

Extensions live in `references/extensions/<category>/<name>/`. Load them lazily to preserve context:

1. **At workflow start**, recursively list `references/extensions/`. Load ONLY `*.opt-in.md` files — each contains a short opt-in prompt. Do NOT load the matching full rule file yet.
2. **During Requirements Analysis**, surface each loaded opt-in prompt as a clarifying question. Record each answer as `Enabled: yes|no` under `## Extension Configuration` in `aidlc-docs/aidlc-state.md`.
3. **On first opt-in** to an extension, derive the rule filename by stripping `.opt-in.md` and appending `.md` (e.g., `security-baseline.opt-in.md` → `security-baseline.md`) and load it. When the user opts out, do NOT load the rule file — saves context.
4. **An extension without a matching `*.opt-in.md`** is always enforced; load its rule file at workflow start.

**Enforcement contract**:

- Extension rules are hard constraints, not optional guidance.
- Before enforcing any extension at ANY stage, re-check its `Enabled` status in `aidlc-docs/aidlc-state.md`. Skip disabled extensions and log the skip in `audit.md`.
- Evaluate which enabled rules are applicable to the current stage's artifacts. Rules that do not apply are marked `N/A` in the stage's compliance summary — this is not a blocking finding.
- Non-compliance with any applicable enabled rule is a **blocking finding** — do NOT present stage completion until resolved.
- Stage completion messages for stages with enabled extensions MUST include a compliance summary (compliant / non-compliant / N/A per rule, with a brief N/A rationale).
- If enabled extensions produce conflicting requirements, present the conflict to the user and ask which takes precedence before proceeding.

Currently bundled extensions:

| Category | Extension              | Opt-in prompt                                                                   | Rules                                                                    |
| -------- | ---------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| security | Security Baseline      | `references/extensions/security/baseline/security-baseline.opt-in.md`           | `references/extensions/security/baseline/security-baseline.md`           |
| testing  | Property-Based Testing | `references/extensions/testing/property-based/property-based-testing.opt-in.md` | `references/extensions/testing/property-based/property-based-testing.md` |

## Audit logging contract

**File**: `aidlc-docs/audit.md`, append-only.

**Tool rule**: Always read-then-append (or edit-append). NEVER overwrite the whole file — this causes duplication and loses history.

**Granularity**:

- Log every user input (prompts, questions, responses) exactly as provided. Never summarize.
- Log every approval prompt you present.
- Log every user response to an approval prompt.
- Log every stage skip decision (including extension-disabled skips).

**Format**:

```markdown
## [Stage Name or Interaction Type]

**Timestamp**: [ISO 8601, YYYY-MM-DDTHH:MM:SSZ]
**User Input**: "[Complete raw user input — never summarized]"
**AI Response**: "[AI's response or action taken]"
**Context**: [Stage, action, or decision. For per-unit stages include unit name, e.g. "CONSTRUCTION - Code Generation - Unit: user-service"]

---
```

## Plan-Level Checkbox Enforcement

When a stage produces a plan file with `- [ ]` checkboxes, **mark each checkbox `[x]` in the same turn where the step's work completed**. No exceptions. This is enforced because unmarked checkboxes silently break session-resume.

Two-level tracking:

- **Plan-level**: detailed execution progress inside each stage's plan file
- **Stage-level**: overall workflow progress in `aidlc-docs/aidlc-state.md`

Update both immediately, in the same turn the work completes.

## Directory structure

Application code goes in the workspace root. Everything AI-DLC produces goes in `aidlc-docs/`. These two sets never mix.

```text
<WORKSPACE-ROOT>/              # Application code lives here
├── [project-specific]
│
└── aidlc-docs/                # Documentation ONLY — never code
    ├── aidlc-state.md
    ├── audit.md
    ├── inception/
    │   ├── plans/
    │   ├── reverse-engineering/   # brownfield only
    │   ├── requirements/
    │   ├── user-stories/
    │   └── application-design/
    ├── construction/
    │   ├── plans/
    │   ├── {unit-name}/
    │   │   ├── functional-design/
    │   │   ├── nfr-requirements/
    │   │   ├── nfr-design/
    │   │   ├── infrastructure-design/
    │   │   └── code/              # markdown summaries only
    │   └── build-and-test/
    └── operations/
```

See `references/construction/code-generation.md` for per-stack project layouts.

## Hard rules (summary)

- **Never proceed without explicit user approval** at a stage's completion message.
- **Code lives in the workspace root, never in `aidlc-docs/`.**
- **Audit is append-only**, captures complete raw user input, uses ISO 8601 timestamps.
- **NO EMERGENT BEHAVIOR**: Construction stages use exactly the 2-option completion message defined in their reference file. Do not invent 3-option menus.
- **Validate every artifact** before writing it per `references/common/content-validation.md`.
- **Every plan checkbox is updated in the same turn the step completes.**
- **Questions use the multiple-choice format with `[Answer]:` tags** from `references/common/question-format-guide.md`.
- **When in doubt, ask the question** — overconfidence (skipping questions, making assumptions) leads to poor outcomes.
- **Overwrite artifacts freely** during normal execution. Archive (`{artifact}.backup.{timestamp}`) only when the user explicitly requests a stage restart.

## Reference file index

Load a file only when you reach the matching trigger described above — the reference file itself says when to load it.

### `references/common/`

- `process-overview.md` — technical workflow overview (MANDATORY at workflow start)
- `welcome-message.md` — user-facing welcome (MANDATORY, display once)
- `session-continuity.md` — session resumption (MANDATORY at workflow start)
- `content-validation.md` — validation rules (MANDATORY before every file creation)
- `question-format-guide.md` — A/B/C/D/E + `[Answer]:` tag format (MANDATORY when asking any question)
- `depth-levels.md` — minimal / standard / comprehensive depth semantics (load during Workflow Planning)
- `error-handling.md` — recovery patterns (load on error)
- `workflow-changes.md` — handling mid-workflow changes (load if the user asks to add/remove/re-run a stage)
- `state-template.md` — scaffold for `aidlc-docs/aidlc-state.md` (load at workflow start)
- `audit-template.md` — scaffold for `aidlc-docs/audit.md` (load at workflow start)

### `references/inception/`

Load each file when its stage runs. Each file contains the stage's Execute-IF/Skip-IF conditions, step-by-step plan, question format, and standardized completion message.

### `references/construction/`

Load each file when its stage runs in the Per-Unit Loop, or for Build and Test once all units are complete. Each file contains the stage's 2-option completion message.

### `references/operations/`

- `operations.md` — placeholder for future deployment / monitoring workflows.

### `references/extensions/`

Load `*.opt-in.md` at workflow start. Load the matching rules file only when the user opts in during Requirements Analysis.
