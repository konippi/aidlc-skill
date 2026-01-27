# NFR Requirements - Detailed Steps

## Overview

Determine Non-Functional Requirements and select technology stack for each unit through two integrated parts:
- **Part 1 - Planning**: Identify NFR categories and create analysis plan
- **Part 2 - Generation**: Execute approved plan to document NFRs and tech stack decisions

## Prerequisites

- Functional Design must be complete for the unit (if executed)
- Unit boundaries and responsibilities must be clear
- Business requirements must be understood

---

# PART 1: PLANNING

## Step 1: Analyze Unit Context

- [ ] Read functional design artifacts (if available)
- [ ] Identify unit's operational characteristics
- [ ] Review system-wide NFR constraints
- [ ] Identify integration requirements

## Step 2: Create NFR Analysis Plan

- [ ] Identify relevant NFR categories:
  - Performance (response time, throughput)
  - Scalability (load handling, growth)
  - Security (authentication, authorization, data protection)
  - Reliability (availability, fault tolerance)
  - Maintainability (code quality, documentation)
  - Observability (logging, monitoring, tracing)
- [ ] Create explicit steps for analysis
- [ ] Number each step sequentially
- [ ] Add checkboxes [ ] for each step

## Step 3: Generate Context-Appropriate Questions

Generate questions using [Answer]: tag format:

```markdown
### Performance Requirements

**Q1**: What are the expected response time requirements?
[Answer]: 

**Q2**: What is the expected throughput (requests/second)?
[Answer]: 

### Security Requirements

**Q3**: What authentication mechanism is required?
[Answer]: 

**Q4**: What data needs to be encrypted?
[Answer]: 

### Scalability Requirements

**Q5**: What is the expected user/load growth?
[Answer]: 

### Technology Preferences

**Q6**: Are there any technology constraints or preferences?
[Answer]: 
```

## Step 4: Collect and Analyze Answers

- [ ] Wait for user to provide answers
- [ ] Analyze answers for completeness
- [ ] Generate follow-up questions if needed
- [ ] Identify technology implications

## Step 5: Create Plan Document

Save complete plan as `aidlc-docs/construction/plans/{unit-name}-nfr-requirements-plan.md`

## Step 6: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**


---

# PART 2: GENERATION

## Step 7: Load NFR Requirements Plan

- [ ] Read the complete plan
- [ ] Identify the next uncompleted step
- [ ] Load the context for that step

## Step 8: Execute Current Step

Generate NFR artifacts based on current step:

### Performance Requirements
- Response time targets
- Throughput requirements
- Resource utilization limits

### Security Requirements
- Authentication requirements
- Authorization model
- Data protection requirements
- Compliance requirements

### Scalability Requirements
- Horizontal/vertical scaling needs
- Load balancing requirements
- Caching strategy

### Technology Stack Selection
- Language/framework selection with rationale
- Database selection with rationale
- Infrastructure components
- Third-party services

## Step 9: Update Progress

- [ ] Mark the completed step as [x] in the plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save generated artifacts

## Step 10: Continue or Complete

- [ ] If more steps remain, return to Step 7
- [ ] If all steps complete, proceed to completion message

## Step 11: Present Completion Message

```markdown
# ⚡ NFR Requirements Complete - [unit-name]

[AI-generated summary]
- Performance requirements defined
- Security requirements documented
- Technology stack selected

> **📋 REVIEW REQUIRED:**  
> Please examine: `aidlc-docs/construction/[unit-name]/nfr-requirements/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications
> ✅ **Continue to Next Stage** - Proceed to **NFR Design**
```

## Step 12: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**

## Step 13: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark NFR Requirements stage as complete for this unit

---

## Output Artifacts

- `aidlc-docs/construction/{unit-name}/nfr-requirements/performance.md`
- `aidlc-docs/construction/{unit-name}/nfr-requirements/security.md`
- `aidlc-docs/construction/{unit-name}/nfr-requirements/scalability.md`
- `aidlc-docs/construction/{unit-name}/nfr-requirements/tech-stack.md`

## Critical Rules

- **FOLLOW PLAN EXACTLY**: Do not deviate from approved steps
- **JUSTIFY DECISIONS**: All tech stack choices must have rationale
- **EXPLICIT APPROVAL**: Never proceed without user approval
