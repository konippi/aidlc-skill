# Mid-Workflow Changes

Handle user requests to alter the execution plan during a workflow.

## Change Types

### 1. Add a skipped stage

1. Confirm request and explain what it adds
2. Check prerequisites are met
3. Add to plan, execute normally
4. Log in `audit.md`

### 2. Skip a planned stage

1. Warn about downstream impact (what will be missing)
2. Get explicit confirmation
3. Mark "SKIPPED" in `aidlc-state.md`
4. Log reason in `audit.md`

### 3. Restart current stage

1. Ask what specifically to change — offer modify vs. full restart
2. If restart: archive existing artifacts, reset checkboxes, re-execute
3. Log reason

### 4. Restart a previous stage

1. Identify all dependent stages that must also be redone
2. Warn user of full cascading impact
3. Get explicit confirmation
4. Archive all affected artifacts, reset all affected stages
5. Resume from that stage

### 5. Change depth level

1. Confirm new depth (minimal/standard/comprehensive)
2. Update execution plan
3. Can only change before or during stage, not after completion

### 6. Pause workflow

1. Complete current step if possible
2. Update all checkboxes and `aidlc-state.md`
3. Log pause point — on resume, session-continuity.md handles detection

### 7. Change architectural decision

- Before Units Generation: minimal impact, update decision
- After Units Generation: must redo units + all per-unit design
- After Code Generation: significant rework — consider cost vs benefit

### 8. Add/remove/split units

1. Assess which units have completed design/code
2. Update unit artifacts (`unit-of-work.md`, dependencies, story map)
3. Reset affected units, execute design+code for them

## General Rules

- **Always confirm** before destructive changes
- **Always archive** before overwriting (`{artifact}.backup.{timestamp}`)
- **Always log** the change, reason, and impact in `audit.md`
- **Always update** `aidlc-state.md` to reflect new reality

## Logging Format

```markdown
## Change Request - [Stage Name]
**Timestamp**: [ISO 8601]
**Request**: [What user wants]
**Impact**: [What will be affected]
**Action**: [What was done]

---
```
