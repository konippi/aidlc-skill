# Units Generation - Detailed Steps

## Overview

Decompose the system into manageable units of work. This stage is CONDITIONAL.

**DEFINITION**: A unit of work is a logical grouping of stories for development purposes. For microservices, each unit becomes an independently deployable service. For monoliths, the single unit represents the entire application with logical modules.

## Prerequisites

- Requirements Analysis must be complete
- Application Design must be complete (if executed)
- Workflow Planning must indicate Units Generation should execute

## Execution Triggers

**Execute IF**:
- System needs decomposition into multiple units of work
- Multiple services or modules required
- Complex system requiring structured breakdown

**Skip IF**:
- Single simple unit
- No decomposition needed
- Straightforward single-component implementation

---

# PART 1: PLANNING

## Step 1: Create Unit of Work Plan

Generate plan with checkboxes [ ] for decomposing system into units of work.

## Step 2: Include Mandatory Unit Artifacts in Plan

- [ ] Generate `aidlc-docs/inception/application-design/unit-of-work.md` with unit definitions
- [ ] Generate `aidlc-docs/inception/application-design/unit-of-work-dependency.md` with dependency matrix
- [ ] Generate `aidlc-docs/inception/application-design/unit-of-work-story-map.md` mapping stories to units
- [ ] **Greenfield only**: Document code organization strategy
- [ ] Validate unit boundaries and dependencies
- [ ] Ensure all stories are assigned to units

## Step 3: Generate Context-Appropriate Questions

**Question categories** (adapt as needed):
- **Story Grouping**: How to group stories into units
- **Dependencies**: Integration approach between units
- **Team Alignment**: Team structure or ownership
- **Technical Considerations**: Scalability/deployment requirements
- **Business Domain**: Domain boundaries or bounded contexts
- **Code Organization** (greenfield multi-unit): Deployment model and directory structure

Use [Answer]: tag format for all questions.

## Step 4: Store Plan

Save as `aidlc-docs/inception/plans/unit-of-work-plan.md`

## Step 5: Request User Input

Ask user to fill [Answer]: tags directly in the plan document.

## Step 6: Analyze Answers

Check for ambiguities:
- Vague responses
- Undefined criteria
- Contradictory answers

## Step 7: Create Follow-up Questions (if needed)

If ANY ambiguities found, create follow-up questions. **DO NOT proceed until resolved.**

## Step 8: Wait for Plan Approval

Ask: "**Unit of work plan complete. Review the plan. Ready to proceed to generation?**"

**DO NOT PROCEED until user confirms.**


---

# PART 2: GENERATION

## Step 9: Load Unit of Work Plan

- Read the complete plan from `aidlc-docs/inception/plans/unit-of-work-plan.md`
- Identify the next uncompleted step

## Step 10: Execute Current Step

- Perform exactly what the current step describes
- Generate unit artifacts as specified
- Follow the approved decomposition approach

## Step 11: Update Progress

- Mark the completed step as [x] in the plan
- Update `aidlc-docs/aidlc-state.md`
- Save all generated artifacts

## Step 12: Continue or Complete

- If more steps remain, return to Step 9
- If all steps complete, proceed to completion message

## Step 13: Present Completion Message

```markdown
# 🔧 Units Generation Complete

[AI-generated summary of units and decomposition]

**Units Created**:
- [unit-1]: [description]
- [unit-2]: [description]

> **📋 REVIEW REQUIRED:**  
> Please examine the units generation artifacts at: `aidlc-docs/inception/application-design/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the units
> ✅ **Approve & Continue** - Approve units and proceed to **CONSTRUCTION PHASE**
```

## Step 14: Wait for Explicit Approval

- **DO NOT PROCEED until user confirms**
- Log approval in audit.md with timestamp
- Mark Units Generation stage complete in aidlc-state.md

## Critical Rules

- **ALWAYS** follow Planning → Generation pattern
- **NEVER** proceed with ambiguous answers
- **ALWAYS** ensure all stories are assigned to units
- **ALWAYS** wait for explicit approval at both stages
