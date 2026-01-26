# Reverse Engineering - Detailed Steps

## Overview

Analyze existing codebase to understand architecture, components, and technology stack. This stage is CONDITIONAL - executes only for brownfield projects.

## Prerequisites

- Workspace Detection must be complete
- Project type must be brownfield
- No previous reverse engineering artifacts found

## Execution Triggers

**Execute IF**:
- Existing codebase detected
- No previous reverse engineering artifacts found

**Skip IF**:
- Greenfield project
- Previous reverse engineering artifacts exist

## Execution Steps

### Step 1: Log Start

**MANDATORY**: Log start of reverse engineering in `aidlc-docs/audit.md`

### Step 2: Analyze Codebase

Perform comprehensive analysis:
- Scan all packages and components
- Identify architectural patterns
- Map dependencies
- Document APIs
- Identify technology stack

### Step 3: Generate Business Overview

Create a business overview covering:
- Business transactions
- Core workflows
- Domain concepts

### Step 4: Generate Architecture Documentation

Create `aidlc-docs/inception/reverse-engineering/architecture.md`:
- High-level architecture diagram
- Architectural patterns used
- System boundaries
- External integrations

### Step 5: Generate Component Inventory

Create `aidlc-docs/inception/reverse-engineering/component-inventory.md`:
- List of all components
- Component responsibilities
- Component relationships

### Step 6: Generate Code Structure Documentation

Create `aidlc-docs/inception/reverse-engineering/code-structure.md`:
- Directory structure
- Module organization
- Key files and their purposes


### Step 7: Generate API Documentation

Create `aidlc-docs/inception/reverse-engineering/api-documentation.md`:
- API endpoints
- Request/response formats
- Authentication methods

### Step 8: Generate Interaction Diagrams

Document how business transactions are implemented across components:
- Sequence diagrams
- Data flow diagrams

### Step 9: Generate Technology Stack Documentation

Create `aidlc-docs/inception/reverse-engineering/technology-stack.md`:
- Languages and frameworks
- Libraries and dependencies
- Build tools
- Testing frameworks

### Step 10: Generate Dependencies Documentation

Create `aidlc-docs/inception/reverse-engineering/dependencies.md`:
- External dependencies
- Internal dependencies
- Dependency versions

### Step 11: Present Completion Message

```markdown
# 🔍 Reverse Engineering Complete

[AI-generated summary of findings]

**Architecture**: [summary]
**Components**: [count] components identified
**Technology Stack**: [key technologies]

> **📋 REVIEW REQUIRED:**  
> Please examine the reverse engineering artifacts at: `aidlc-docs/inception/reverse-engineering/`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications or additional analysis
> ✅ **Approve & Continue** - Approve analysis and proceed to **Requirements Analysis**
```

### Step 12: Wait for Explicit Approval

- **DO NOT PROCEED until user confirms**
- Log approval in audit.md with timestamp
- Update Reverse Engineering stage complete in aidlc-state.md

## Critical Rules

- **ALWAYS** analyze all packages and components
- **ALWAYS** generate all required artifacts
- **ALWAYS** wait for explicit approval before proceeding
- **ALWAYS** log user's response in audit.md
