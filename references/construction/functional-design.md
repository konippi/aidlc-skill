# Functional Design - Detailed Steps

## Overview

Create detailed business logic design for each unit of work through two integrated parts:
- **Part 1 - Planning**: Create functional design plan with explicit steps
- **Part 2 - Generation**: Execute approved plan to generate detailed design artifacts

## Prerequisites

- Workflow Planning must be complete
- Unit of work must be defined
- Requirements and user stories (if applicable) must be available

---

# PART 1: PLANNING

## Step 1: Analyze Unit Context

- [ ] Read unit definition from workflow plan
- [ ] Read assigned user stories for this unit
- [ ] Identify unit boundaries and responsibilities
- [ ] Review requirements relevant to this unit

## Step 2: Create Functional Design Plan

- [ ] Identify data models and entities for this unit
- [ ] Identify business rules and validation logic
- [ ] Identify service interfaces and contracts
- [ ] Identify integration points with other units
- [ ] Create explicit steps for design:
  - Data Model Design
  - Business Rules Definition
  - Service Interface Design
  - State Machine Design (if applicable)
  - Error Handling Strategy
  - Validation Rules
- [ ] Number each step sequentially
- [ ] Add checkboxes [ ] for each step

## Step 3: Generate Context-Appropriate Questions

Generate questions using [Answer]: tag format:

```markdown
### Data Model Questions

**Q1**: What are the core entities for this unit?
[Answer]: 

**Q2**: What relationships exist between entities?
[Answer]: 

### Business Logic Questions

**Q3**: What are the key business rules?
[Answer]: 

**Q4**: What validation is required for inputs?
[Answer]: 
```

## Step 4: Collect and Analyze Answers

- [ ] Wait for user to provide answers
- [ ] Analyze answers for ambiguities or gaps
- [ ] Generate follow-up questions if needed
- [ ] Repeat until requirements are clear

## Step 5: Create Plan Document

Save complete plan as `aidlc-docs/construction/plans/{unit-name}-functional-design-plan.md`

## Step 6: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**
- If user requests changes, update the plan and repeat approval process


---

# PART 2: GENERATION

## Step 7: Load Functional Design Plan

- [ ] Read the complete plan from `aidlc-docs/construction/plans/{unit-name}-functional-design-plan.md`
- [ ] Identify the next uncompleted step
- [ ] Load the context for that step

## Step 8: Execute Current Step

Generate design artifacts based on current step:

### Data Model Design
- Entity definitions with attributes
- Relationships and cardinality
- Data types and constraints

### Business Rules Definition
- Rule specifications
- Preconditions and postconditions
- Exception scenarios

### Service Interface Design
- Method signatures
- Input/output contracts
- Error responses

## Step 9: Update Progress

- [ ] Mark the completed step as [x] in the plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save generated artifacts to `aidlc-docs/construction/{unit-name}/functional-design/`

## Step 10: Continue or Complete

- [ ] If more steps remain, return to Step 7
- [ ] If all steps complete, proceed to completion message

## Step 11: Present Completion Message

```markdown
# 📐 Functional Design Complete - [unit-name]

[AI-generated summary]
- Data models defined
- Business rules documented
- Service interfaces specified

> **📋 REVIEW REQUIRED:**  
> Please examine: `aidlc-docs/construction/[unit-name]/functional-design/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications
> ✅ **Continue to Next Stage** - Proceed to **NFR Requirements**
```

## Step 12: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**

## Step 13: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark Functional Design stage as complete for this unit

---

## Output Artifacts

- `aidlc-docs/construction/{unit-name}/functional-design/data-models.md`
- `aidlc-docs/construction/{unit-name}/functional-design/business-rules.md`
- `aidlc-docs/construction/{unit-name}/functional-design/service-interfaces.md`

## Critical Rules

- **FOLLOW PLAN EXACTLY**: Do not deviate from approved steps
- **UPDATE CHECKBOXES**: Mark [x] immediately after completion
- **EXPLICIT APPROVAL**: Never proceed without user approval
