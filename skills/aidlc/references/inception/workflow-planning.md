# Workflow Planning - Detailed Steps

## Overview

Create execution plan showing which stages to run and why. This stage ALWAYS executes.

## Prerequisites

- Workspace Detection must be complete
- Requirements Analysis must be complete
- User Stories complete (if executed)

## Execution Steps

### Step 1: Load All Prior Context

Load all available context:
- Reverse engineering artifacts (if brownfield)
- Intent analysis from Requirements Analysis
- Requirements document
- User stories (if executed)

### Step 2: Analyze Complexity and Risk

Evaluate:
- **Scope**: Single file → System-wide
- **Complexity**: Trivial → Complex
- **Risk**: Low → High
- **Stakeholders**: Single → Multiple
- **Dependencies**: None → Many

### Step 3: Determine Stage Execution

For each conditional stage, determine if it should execute:

**Application Design**:
- Execute IF: New components/services needed, service layer design required
- Skip IF: Changes within existing component boundaries

**Units Generation**:
- Execute IF: System needs decomposition into multiple units
- Skip IF: Single simple unit, no decomposition needed

**Functional Design** (per-unit):
- Execute IF: New data models, complex business logic
- Skip IF: Simple logic changes

**NFR Requirements** (per-unit):
- Execute IF: Performance, security, scalability requirements
- Skip IF: No NFR requirements

**NFR Design** (per-unit):
- Execute IF: NFR Requirements was executed
- Skip IF: NFR Requirements was skipped

**Infrastructure Design** (per-unit):
- Execute IF: Infrastructure services need mapping
- Skip IF: No infrastructure changes

### Step 4: Determine Depth Levels

For each stage to execute, determine depth:
- **Minimal**: Clear, simple request
- **Standard**: Normal complexity
- **Comprehensive**: Complex, high-risk


### Step 5: Create Workflow Plan Document

Create `aidlc-docs/inception/plans/workflow-plan.md`:

```markdown
# AI-DLC Workflow Plan

## Project Summary
- **Project Type**: [greenfield/brownfield]
- **Complexity**: [trivial/simple/moderate/complex]
- **Risk Level**: [low/medium/high]

## Execution Plan

### 🔵 INCEPTION PHASE
| Stage | Execute | Depth | Reason |
|-------|---------|-------|--------|
| Workspace Detection | ✅ Complete | - | Always executes |
| Reverse Engineering | [✅/⏭️] | - | [reason] |
| Requirements Analysis | ✅ Complete | [depth] | Always executes |
| User Stories | [✅/⏭️] | [depth] | [reason] |
| Workflow Planning | ✅ In Progress | - | Always executes |
| Application Design | [✅/⏭️] | [depth] | [reason] |
| Units Generation | [✅/⏭️] | [depth] | [reason] |

### 🟢 CONSTRUCTION PHASE
| Stage | Execute | Depth | Reason |
|-------|---------|-------|--------|
| Functional Design | [✅/⏭️] | [depth] | [reason] |
| NFR Requirements | [✅/⏭️] | [depth] | [reason] |
| NFR Design | [✅/⏭️] | [depth] | [reason] |
| Infrastructure Design | [✅/⏭️] | [depth] | [reason] |
| Code Generation | ✅ | [depth] | Always executes |
| Build and Test | ✅ | - | Always executes |

## Units of Work
[List units if multiple, or "Single unit" if one]

## Estimated Stages
- Total stages to execute: [count]
- Stages skipped: [count]
```

### Step 6: Validate Content

**MANDATORY**: Validate all content before file creation:
- Validate Mermaid diagram syntax (if any)
- Validate ASCII art diagrams
- Escape special characters properly

### Step 7: Log Approval Prompt

Log the approval prompt with timestamp in `aidlc-docs/audit.md`

### Step 8: Present Completion Message

```markdown
# 📋 Workflow Planning Complete

[AI-generated summary of execution plan]

**Stages to Execute**: [list]
**Stages Skipped**: [list with reasons]

> **📋 REVIEW REQUIRED:**  
> Please examine the workflow plan at: `aidlc-docs/inception/plans/workflow-plan.md`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Modify which stages execute or their depth
> ➕ **Add Stage** - Include a skipped stage
> ➖ **Remove Stage** - Skip a planned stage
> ✅ **Approve & Continue** - Approve plan and proceed to **[Application Design/Units Generation/Construction Phase]**
```

### Step 9: Wait for Explicit Approval

- **DO NOT PROCEED until user confirms**
- User can override recommendations (add/remove stages)
- Log approval response with timestamp
- Update Workflow Planning stage complete in aidlc-state.md

### Step 10: Determine Next Stage

Based on approved plan:
- If Application Design to execute → Application Design
- Else if Units Generation to execute → Units Generation
- Else → Construction Phase

## Critical Rules

- **ALWAYS** provide clear reasoning for each stage decision
- **ALWAYS** allow user to override recommendations
- **ALWAYS** validate content before file creation
- **ALWAYS** wait for explicit approval
