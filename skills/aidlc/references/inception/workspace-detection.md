# Workspace Detection - Detailed Steps

## Overview

Analyze workspace state and determine project type. This stage ALWAYS executes as the first step of any AI-DLC workflow.

## Prerequisites

- AI-DLC workflow initialized
- `aidlc-docs/aidlc-state.md` created
- `aidlc-docs/audit.md` created

## Execution Steps

### Step 1: Log Initial User Request

**MANDATORY**: Log the complete raw user input in `aidlc-docs/audit.md`

```markdown
## Workflow Initialization
**Timestamp**: [ISO 8601 timestamp]
**User Input**: "[Complete raw user input - NEVER summarize]"
**AI Response**: "Starting Workspace Detection"
**Context**: Initial request logged
```

### Step 2: Check for Existing State

- Look for existing `aidlc-docs/aidlc-state.md`
- If found, check if workflow can be resumed
- If resuming, load previous state and continue from last checkpoint

### Step 3: Scan Workspace

Analyze the workspace for:
- Existing source code files
- Package managers (package.json, pom.xml, requirements.txt, etc.)
- Build configurations
- Test files
- Documentation

### Step 4: Determine Project Type

**Greenfield Project**:
- No existing source code
- Empty or minimal workspace
- New project from scratch

**Brownfield Project**:
- Existing source code detected
- Established project structure
- Existing dependencies and configurations

### Step 5: Check for Reverse Engineering Artifacts

If brownfield, check for existing artifacts:
- `aidlc-docs/inception/reverse-engineering/architecture.md`
- `aidlc-docs/inception/reverse-engineering/component-inventory.md`
- `aidlc-docs/inception/reverse-engineering/technology-stack.md`

### Step 6: Log Findings

Update `aidlc-docs/audit.md` with detection results.

### Step 7: Update State

Update `aidlc-docs/aidlc-state.md`:
- Set Project Type
- Set Workspace Root
- Mark Workspace Detection as complete


### Step 8: Present Completion Message

**For Greenfield**:
```markdown
# 🔍 Workspace Detection Complete

**Project Type**: Greenfield (new project)
**Workspace**: [path]

No existing codebase detected. Starting fresh.

Proceeding to **Requirements Analysis**...
```

**For Brownfield**:
```markdown
# 🔍 Workspace Detection Complete

**Project Type**: Brownfield (existing project)
**Workspace**: [path]
**Detected Technologies**: [list]

Existing codebase detected. [Will analyze / Already analyzed].

Proceeding to **[Reverse Engineering / Requirements Analysis]**...
```

### Step 9: Determine Next Stage

- If brownfield AND no reverse engineering artifacts → Reverse Engineering
- Otherwise → Requirements Analysis

## Critical Rules

- **ALWAYS** log initial user request with complete raw input
- **ALWAYS** check for existing state before starting fresh
- **ALWAYS** update aidlc-state.md after completion
- Automatically proceed to next stage (no approval needed for this stage)
