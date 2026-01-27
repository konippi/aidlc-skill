# Session Continuity

## Overview

Session continuity ensures AI-DLC workflow can be resumed after interruptions, maintaining state and progress across sessions.

## State Management

### Primary State File

`aidlc-docs/aidlc-state.md` is the source of truth for workflow state:

```markdown
# AI-DLC Workflow State

## Workflow Information
- **Started**: [ISO 8601 timestamp]
- **Last Updated**: [ISO 8601 timestamp]
- **Project Type**: [greenfield/brownfield]
- **Depth Level**: [minimal/standard/comprehensive]

## Current Status
- **Phase**: [Inception/Construction/Operations]
- **Stage**: [Current stage name]
- **Status**: [In Progress/Awaiting Approval/Complete]

## Progress
### Inception Phase
- [x] Workspace Detection - Complete
- [x] Requirements Analysis - Complete
- [ ] User Stories - In Progress
- [ ] Workflow Planning - Not Started

### Construction Phase
- [ ] Unit 1: [unit-name]
  - [ ] Functional Design
  - [ ] NFR Requirements
  - [ ] Code Generation
- [ ] Build and Test
```

### State Updates

Update state file:
- After each step completion
- After each stage completion
- After each user approval
- When status changes

---

## Session Recovery

### Detecting Interrupted Session

When starting AI-DLC, check for existing state:

1. Check if `aidlc-docs/aidlc-state.md` exists
2. If exists, read current state
3. Determine if workflow is in progress

### Recovery Prompt

If interrupted session detected:

```markdown
# 🔄 AI-DLC Session Recovery

I found an existing AI-DLC workflow in progress:

**Project**: [project name]
**Phase**: [current phase]
**Stage**: [current stage]
**Status**: [current status]
**Last Updated**: [timestamp]

Would you like to:
1. **Resume** - Continue from where we left off
2. **Restart** - Start a new workflow (existing progress will be archived)
3. **Review** - Show me the current state before deciding
```

### Resume Workflow

When resuming:

1. Load state from `aidlc-state.md`
2. Load audit trail from `audit.md`
3. Identify next action based on status:
   - **In Progress**: Continue current step
   - **Awaiting Approval**: Re-present approval prompt
   - **Complete**: Move to next stage

### Restart Workflow

When restarting:

1. Archive existing `aidlc-docs/` to `aidlc-docs-archive-[timestamp]/`
2. Create fresh `aidlc-docs/` directory
3. Initialize new state and audit files
4. Begin workflow from Workspace Detection

---

## Audit Trail Recovery

### Audit File Structure

`aidlc-docs/audit.md` maintains complete interaction history:

```markdown
# AI-DLC Audit Trail

## Session: [session-id]
Started: [ISO 8601 timestamp]

### [timestamp] - Workspace Detection
[Complete interaction log]

### [timestamp] - Requirements Analysis - Questions
[Questions presented]

### [timestamp] - Requirements Analysis - Answers
[User answers - complete raw input]

### [timestamp] - Requirements Analysis - Approval
User approved requirements analysis plan.
```

### Using Audit for Recovery

When recovering:
1. Read audit trail
2. Identify last logged interaction
3. Determine what was presented to user
4. Resume from appropriate point

---

## Handling Partial Completion

### Mid-Step Interruption

If interrupted during step execution:
1. Check for partial artifacts
2. Validate completeness
3. Either complete the step or restart it

### Mid-Stage Interruption

If interrupted between steps:
1. Load stage plan
2. Find last completed step (marked [x])
3. Continue from next uncompleted step

### Mid-Phase Interruption

If interrupted between stages:
1. Load state file
2. Find last completed stage
3. Continue from next stage

---

## State Validation

### On Session Start

Validate state consistency:

- [ ] State file exists and is readable
- [ ] Audit file exists and is readable
- [ ] Current stage matches audit trail
- [ ] Referenced artifacts exist
- [ ] No orphaned artifacts

### Inconsistency Handling

If inconsistency detected:

```markdown
⚠️ **State Inconsistency Detected**

The workflow state appears inconsistent:
- [Description of inconsistency]

Recommended action:
1. **Auto-repair** - Attempt to fix based on audit trail
2. **Manual review** - Show details for manual resolution
3. **Restart** - Begin fresh workflow
```

---

## Best Practices

### For Users

1. **Don't manually edit state files** - Let AI-DLC manage state
2. **Review audit trail** if unsure of progress
3. **Use "Resume" option** when returning to interrupted workflow

### For AI-DLC

1. **Update state immediately** after each action
2. **Log everything** in audit trail
3. **Validate state** before proceeding
4. **Handle interruptions gracefully**

---

## Critical Rules

1. **ALWAYS check for existing state** before starting
2. **ALWAYS offer recovery options** if state exists
3. **NEVER lose user progress** - state must be persistent
4. **ALWAYS validate state** before resuming
5. **ARCHIVE, don't delete** when restarting
