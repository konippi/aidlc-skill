# NFR Design - Detailed Steps

## Overview

Incorporate NFR patterns into the design for each unit through two integrated parts:
- **Part 1 - Planning**: Create NFR implementation design plan
- **Part 2 - Generation**: Execute approved plan to generate NFR design artifacts

## Prerequisites

- NFR Requirements must be complete for the unit
- Technology stack must be selected
- Functional design must be available

---

# PART 1: PLANNING

## Step 1: Analyze NFR Requirements

- [ ] Read NFR requirements from previous stage
- [ ] Read selected technology stack
- [ ] Identify patterns needed for each NFR category
- [ ] Review functional design for integration points

## Step 2: Create NFR Design Plan

- [ ] Map NFRs to implementation patterns:
  - Performance patterns (caching, connection pooling, async processing)
  - Security patterns (authentication flows, authorization checks, encryption)
  - Scalability patterns (horizontal scaling, load balancing, sharding)
  - Reliability patterns (circuit breaker, retry, fallback)
  - Observability patterns (structured logging, metrics, distributed tracing)
- [ ] Create explicit steps for design
- [ ] Number each step sequentially
- [ ] Add checkboxes [ ] for each step

## Step 3: Generate Context-Appropriate Questions

Generate questions using [Answer]: tag format:

```markdown
### Performance Design

**Q1**: What caching strategy should be used?
[Answer]: 

**Q2**: Are there any async processing requirements?
[Answer]: 

### Security Design

**Q3**: What authentication flow is preferred?
[Answer]: 

### Reliability Design

**Q4**: What retry/fallback strategies are needed?
[Answer]: 
```

## Step 4: Collect and Analyze Answers

- [ ] Wait for user to provide answers
- [ ] Analyze answers for completeness
- [ ] Generate follow-up questions if needed

## Step 5: Create Plan Document

Save complete plan as `aidlc-docs/construction/plans/{unit-name}-nfr-design-plan.md`

## Step 6: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**


---

# PART 2: GENERATION

## Step 7: Load NFR Design Plan

- [ ] Read the complete plan
- [ ] Identify the next uncompleted step
- [ ] Load the context for that step

## Step 8: Execute Current Step

Generate NFR design artifacts based on current step:

### Performance Design
- Caching layer design
- Connection pool configuration
- Async processing design
- Query optimization strategies

### Security Design
- Authentication flow diagrams
- Authorization matrix
- Encryption implementation
- Security middleware design

### Scalability Design
- Horizontal scaling architecture
- Load balancer configuration
- Database sharding strategy
- Message queue design

### Reliability Design
- Circuit breaker configuration
- Retry policies
- Fallback strategies
- Health check design

### Observability Design
- Logging format and levels
- Metrics collection points
- Distributed tracing setup
- Alerting rules

## Step 9: Update Progress

- [ ] Mark the completed step as [x] in the plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save generated artifacts

## Step 10: Continue or Complete

- [ ] If more steps remain, return to Step 7
- [ ] If all steps complete, proceed to completion message

## Step 11: Present Completion Message

```markdown
# 🛡️ NFR Design Complete - [unit-name]

[AI-generated summary]
- Performance patterns designed
- Security implementation planned
- Reliability patterns incorporated

> **📋 REVIEW REQUIRED:**  
> Please examine: `aidlc-docs/construction/[unit-name]/nfr-design/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications
> ✅ **Continue to Next Stage** - Proceed to **Infrastructure Design**
```

## Step 12: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**

## Step 13: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark NFR Design stage as complete for this unit

---

## Output Artifacts

- `aidlc-docs/construction/{unit-name}/nfr-design/performance-design.md`
- `aidlc-docs/construction/{unit-name}/nfr-design/security-design.md`
- `aidlc-docs/construction/{unit-name}/nfr-design/scalability-design.md`
- `aidlc-docs/construction/{unit-name}/nfr-design/reliability-design.md`
- `aidlc-docs/construction/{unit-name}/nfr-design/observability-design.md`

## Critical Rules

- **PATTERN-BASED**: Use established patterns for NFR implementation
- **TECHNOLOGY-ALIGNED**: Patterns must align with selected tech stack
- **EXPLICIT APPROVAL**: Never proceed without user approval
