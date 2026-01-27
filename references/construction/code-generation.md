# Code Generation - Detailed Steps

## Overview

Generate code for each unit of work through two integrated parts:
- **Part 1 - Planning**: Create detailed code generation plan with explicit steps
- **Part 2 - Generation**: Execute approved plan to generate code, tests, and artifacts

**Note**: For brownfield projects, "generate" means modify existing files when appropriate, not create duplicates.

## Prerequisites

- Unit Design Generation must be complete for the unit (if executed)
- NFR Implementation must be complete for the unit (if executed)
- All unit design artifacts must be available
- Unit is ready for code generation

---

# PART 1: PLANNING

## Step 1: Analyze Unit Context

- [ ] Read unit design artifacts from previous stages
- [ ] Read unit story map to understand assigned stories
- [ ] Identify unit dependencies and interfaces
- [ ] Validate unit is ready for code generation

## Step 2: Create Detailed Unit Code Generation Plan

- [ ] Read workspace root and project type from `aidlc-docs/aidlc-state.md`
- [ ] Determine code location (see Code Location Rules below)
- [ ] **Brownfield only**: Review reverse engineering code-structure.md for existing files to modify
- [ ] Document exact paths (never aidlc-docs/)
- [ ] Create explicit steps for unit generation:
  - Project Structure Setup (greenfield only)
  - Business Logic Generation
  - Business Logic Unit Testing
  - Business Logic Summary
  - API Layer Generation
  - API Layer Unit Testing
  - API Layer Summary
  - Repository Layer Generation
  - Repository Layer Unit Testing
  - Repository Layer Summary
  - Database Migration Scripts (if data models exist)
  - Documentation Generation (API docs, README updates)
  - Deployment Artifacts Generation
- [ ] Number each step sequentially
- [ ] Include story mapping references
- [ ] Add checkboxes [ ] for each step

## Step 3: Include Unit Generation Context

For this unit, include:
- Stories implemented by this unit
- Dependencies on other units/services
- Expected interfaces and contracts
- Database entities owned by this unit
- Service boundaries and responsibilities

## Step 4: Create Unit Plan Document

Save complete plan as `aidlc-docs/construction/plans/{unit-name}-code-generation-plan.md`

## Step 5: Summarize Unit Plan

Provide summary of the unit code generation plan to the user:
- Highlight unit generation approach
- Explain step sequence and story coverage
- Note total number of steps and estimated scope

## Step 6: Log Approval Prompt

Log the prompt with timestamp in `aidlc-docs/audit.md`

## Step 7: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**
- If user requests changes, update the plan and repeat approval process

## Step 8: Update Progress

Mark Code Planning complete in `aidlc-state.md`


---

# PART 2: GENERATION

## Step 9: Load Unit Code Generation Plan

- [ ] Read the complete plan from `aidlc-docs/construction/plans/{unit-name}-code-generation-plan.md`
- [ ] Identify the next uncompleted step (first [ ] checkbox)
- [ ] Load the context for that step

## Step 10: Execute Current Step

- [ ] Verify target directory from plan (never aidlc-docs/)
- [ ] **Brownfield only**: Check if target file exists
- [ ] Generate exactly what the current step describes:
  - **If file exists**: Modify it in-place (never create `ClassName_modified.java`)
  - **If file doesn't exist**: Create new file
- [ ] Write to correct locations:
  - **Application Code**: Workspace root per project structure
  - **Documentation**: `aidlc-docs/construction/{unit-name}/code/` (markdown only)
  - **Build/Config Files**: Workspace root
- [ ] Follow unit story requirements
- [ ] Respect dependencies and interfaces

## Step 11: Update Progress

- [ ] Mark the completed step as [x] in the unit code generation plan
- [ ] Mark associated unit stories as [x] when their generation is finished
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] **Brownfield only**: Verify no duplicate files created
- [ ] Save all generated artifacts

## Step 12: Continue or Complete Generation

- [ ] If more steps remain, return to Step 9
- [ ] If all steps complete, proceed to completion message

## Step 13: Present Completion Message

```markdown
# 💻 Code Generation Complete - [unit-name]

[AI-generated summary]
- **Brownfield**: Distinguish modified vs created files
  - Modified: `src/services/user-service.ts`
  - Created: `src/services/auth-service.ts`
- **Greenfield**: List created files with paths
- List tests, documentation, deployment artifacts

> **📋 REVIEW REQUIRED:**  
> Please examine the generated code at:
> - **Application Code**: `[actual-workspace-path]`
> - **Documentation**: `aidlc-docs/construction/[unit-name]/code/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the generated code
> ✅ **Continue to Next Stage** - Approve and proceed to **[next-unit/Build & Test]**
```

## Step 14: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**
- If user requests changes, update the code and repeat approval process

## Step 15: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark Code Generation stage as complete for this unit in aidlc-state.md

---

## Code Location Rules

- **Application code**: Workspace root only (NEVER aidlc-docs/)
- **Documentation**: aidlc-docs/ only (markdown summaries)
- **Read workspace root** from aidlc-state.md before generating code

**Structure patterns by project type**:
- **Brownfield**: Use existing structure (e.g., `src/main/java/`, `lib/`, `pkg/`)
- **Greenfield single unit**: `src/`, `tests/`, `config/` in workspace root
- **Greenfield multi-unit (microservices)**: `{unit-name}/src/`, `{unit-name}/tests/`
- **Greenfield multi-unit (monolith)**: `src/{unit-name}/`, `tests/{unit-name}/`

## Critical Rules

- **NO HARDCODED LOGIC**: Only execute what's written in the unit plan
- **FOLLOW PLAN EXACTLY**: Do not deviate from the step sequence
- **UPDATE CHECKBOXES**: Mark [x] immediately after completing each step
- **STORY TRACEABILITY**: Mark unit stories [x] when functionality is implemented
- **RESPECT DEPENDENCIES**: Only implement when unit dependencies are satisfied
