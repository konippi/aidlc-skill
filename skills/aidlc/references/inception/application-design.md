# Application Design - Detailed Steps

## Overview

High-level component identification and service layer design. This stage is CONDITIONAL.

## Prerequisites

- Requirements Analysis must be complete
- User Stories complete (if executed)
- Workflow Planning must indicate Application Design should execute

## Execution Triggers

**Execute IF**:
- New components or services needed
- Component methods and business rules need definition
- Service layer design required
- Component dependencies need clarification

**Skip IF**:
- Changes within existing component boundaries
- No new components or methods
- Pure implementation changes

## Execution Steps

### Step 1: Load Context

- Load requirements document
- Load user stories (if available)
- Load reverse engineering artifacts (if brownfield)

### Step 2: Identify Components

For each functional area:
- Identify required components
- Define component responsibilities
- Determine component boundaries

### Step 3: Define Component Methods

For each component:
- List methods/operations
- Define business rules for each method
- Specify input/output contracts

### Step 4: Design Service Layer

- Identify services that orchestrate business logic
- Define service responsibilities
- Map services to components

### Step 5: Document Dependencies

- Create component dependency matrix
- Identify communication patterns
- Document integration points

### Step 6: Generate Design Artifacts

Create in `aidlc-docs/inception/application-design/`:
- `components.md` - Component definitions and responsibilities
- `methods.md` - Method definitions and business rules
- `services.md` - Service layer design
- `dependencies.md` - Dependency matrix

### Step 7: Present Completion Message

```markdown
# 🏗️ Application Design Complete

[AI-generated summary of components and services]

> **📋 REVIEW REQUIRED:**  
> Please examine the application design at: `aidlc-docs/inception/application-design/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the design
> ✅ **Approve & Continue** - Approve design and proceed to **[Units Generation/Construction Phase]**
```

### Step 8: Wait for Explicit Approval

- **DO NOT PROCEED until user confirms**
- Log approval in audit.md with timestamp
- Update Application Design stage complete in aidlc-state.md

## Critical Rules

- **ALWAYS** align with requirements and user stories
- **ALWAYS** document component boundaries clearly
- **ALWAYS** wait for explicit approval
