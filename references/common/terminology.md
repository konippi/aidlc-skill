# AI-DLC Terminology

## Core Concepts

### AI-DLC (AI-Driven Development Life Cycle)
An adaptive software development workflow that intelligently tailors itself to specific project needs. Consists of three phases: Inception, Construction, and Operations.

### Phase
A major division of the AI-DLC workflow. Each phase has a distinct purpose:
- **Inception**: Determines WHAT to build and WHY
- **Construction**: Determines HOW to build it
- **Operations**: Determines how to DEPLOY and RUN it

### Stage
A specific step within a phase. Stages can be:
- **ALWAYS**: Executed for every project
- **CONDITIONAL**: Executed based on project characteristics

### Unit of Work
A discrete, implementable piece of functionality. Units are:
- Self-contained with clear boundaries
- Independently testable
- Mapped to specific user stories

---

## Project Types

### Greenfield Project
A new project starting from scratch with no existing codebase.

### Brownfield Project
An existing project with established codebase, patterns, and conventions.

---

## Execution Patterns

### Planning → Generation Pattern
The two-part execution pattern used by all stages:
1. **Planning**: Create detailed plan with checkboxes
2. **Generation**: Execute approved plan step by step

### Human-in-the-Loop
The principle that explicit user approval is required at every critical decision point. AI never proceeds autonomously on important decisions.

### Adaptive Execution
The principle that only stages adding value are executed. Depth and scope adjust based on project complexity.

---

## Depth Levels

### Minimal Depth
Lightweight execution for simple, low-risk changes. Documents intent only.

### Standard Depth
Normal execution for typical features. Gathers functional and non-functional requirements.

### Comprehensive Depth
Thorough execution for complex, high-risk changes. Detailed requirements with full traceability.

---

## Artifacts

### aidlc-state.md
The central state file tracking workflow progress, current phase/stage, and configuration.

### audit.md
The complete audit trail logging all interactions with ISO 8601 timestamps.

### Plan Document
A markdown file with numbered steps and checkboxes created during the Planning part of each stage.

### Design Artifact
Documentation generated during design stages (functional design, NFR design, infrastructure design).

---

## Directory Structure

### aidlc-docs/
The documentation directory containing all AI-DLC artifacts. Located at workspace root.

### inception/
Subdirectory for Inception phase artifacts (requirements, user stories, application design).

### construction/
Subdirectory for Construction phase artifacts (plans, unit designs, build results).

### operations/
Subdirectory for Operations phase artifacts (deployment, monitoring).

---

## Question Format

### [Answer]: Tag
The standardized format for collecting user input:
```markdown
**Q1**: [Question text]
[Answer]: 
```

### Follow-Up Questions
Additional questions generated after analyzing initial answers to clarify ambiguities.

---

## Completion Messages

### 2-Option Format
The standardized completion message format offering two choices:
1. Request Changes
2. Continue to Next Stage

---

## Workflow States

### Not Started
Stage has not begun execution.

### In Progress
Stage is currently executing.

### Awaiting Approval
Stage has completed a part and is waiting for user approval.

### Complete
Stage has finished execution with user approval.

### Skipped
Stage was intentionally not executed (conditional stage not triggered).

---

## Code Generation Terms

### In-Place Modification
Modifying an existing file directly rather than creating a copy (brownfield projects).

### Story Mapping
The association between user stories and units of work, tracking which stories are implemented by which units.

### Traceability
The ability to trace requirements through design to implementation and tests.
