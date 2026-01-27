# Process Overview

## AI-DLC Workflow Summary

AI-DLC (AI-Driven Development Life Cycle) is an adaptive software development workflow that intelligently tailors itself to your specific needs.

---

## The Three Phases

### 🔵 INCEPTION PHASE
**Purpose**: Determines WHAT to build and WHY

| Stage | Execution | Description |
|-------|-----------|-------------|
| Workspace Detection | ALWAYS | Analyze workspace state and project type |
| Reverse Engineering | CONDITIONAL | Analyze existing codebase (brownfield only) |
| Requirements Analysis | ALWAYS | Gather and validate requirements (adaptive depth) |
| User Stories | CONDITIONAL | Create user stories and personas |
| Workflow Planning | ALWAYS | Create execution plan |
| Application Design | CONDITIONAL | High-level component and service design |
| Units Generation | CONDITIONAL | Decompose into units of work |

### 🟢 CONSTRUCTION PHASE
**Purpose**: Determines HOW to build it

| Stage | Execution | Description |
|-------|-----------|-------------|
| Functional Design | CONDITIONAL | Detailed business logic design (per-unit) |
| NFR Requirements | CONDITIONAL | Determine NFRs and select tech stack (per-unit) |
| NFR Design | CONDITIONAL | Incorporate NFR patterns (per-unit) |
| Infrastructure Design | CONDITIONAL | Map to infrastructure services (per-unit) |
| Code Generation | ALWAYS | Generate code (per-unit) |
| Build and Test | ALWAYS | Build all units and execute testing |

### 🟡 OPERATIONS PHASE
**Purpose**: How to DEPLOY and RUN it (future expansion)

Currently a placeholder for future deployment and monitoring workflows.

---

## Key Principles

### 1. Adaptive Execution
Only execute stages that add value to your specific request.

### 2. Flexible Depth
Adjust depth based on complexity:
- **Minimal**: Simple, clear requests
- **Standard**: Normal complexity
- **Comprehensive**: Complex, high-risk changes

### 3. Human-in-the-Loop
Explicit approval required at every critical decision point.

### 4. Complete Audit Trail
Log ALL interactions with ISO 8601 timestamps.

### 5. User Control
User can request stage inclusion/exclusion at any time.

---

## Stage Execution Pattern

All stages follow the **Planning → Generation** pattern:

### Part 1: Planning
1. Create plan with checkboxes for each step
2. Generate context-appropriate questions (multiple choice format)
3. Collect user answers in question files
4. Analyze answers for ambiguities
5. Create follow-up questions if ambiguities found
6. Wait for explicit approval

### Part 2: Generation
1. Load approved plan
2. Execute each step sequentially
3. Mark checkboxes [x] immediately after completion
4. Generate artifacts
5. Present completion message
6. Wait for explicit approval

---

## Completion Message Format

All stages use standardized 2-option completion messages:

```markdown
# [Emoji] [Stage Name] Complete

[AI-generated summary in bullet points]

> **📋 REVIEW REQUIRED:**  
> Please examine: `[artifact path]`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications
> ✅ **Continue to Next Stage** - Proceed to **[Next Stage]**
```

**CRITICAL**: Always use standardized 2-option format. DO NOT use emergent 3-option behavior.

---

## Directory Structure

```
<WORKSPACE-ROOT>/
├── [project-specific structure]    # Application code (NEVER in aidlc-docs/)
│
└── aidlc-docs/                     # Documentation only
    ├── inception/
    │   ├── plans/
    │   ├── reverse-engineering/
    │   ├── requirements/
    │   ├── user-stories/
    │   └── application-design/
    ├── construction/
    │   ├── plans/
    │   ├── {unit-name}/
    │   └── build-and-test/
    ├── operations/
    ├── aidlc-state.md
    └── audit.md
```

---

## Critical Rules

1. **NEVER proceed without explicit user approval**
2. **ALWAYS log interactions in audit.md**
3. **NEVER summarize user input in audit log - capture complete raw input**
4. **Application code goes to workspace root, NEVER to aidlc-docs/**
5. **ALWAYS use multiple choice question format with [Answer]: tags**
6. **ALWAYS validate content before file creation**
