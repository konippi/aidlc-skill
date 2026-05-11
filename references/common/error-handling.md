# Error Handling

## General Principles

1. Identify the error and assess if it's blocking
2. Communicate clearly to the user
3. Offer resolution options
4. Log in `audit.md`

## Severity Levels

- **Critical** (workflow cannot continue): missing required files, invalid user input, system errors
- **High** (stage cannot complete): incomplete answers, contradictory responses, missing dependencies from prior stages
- **Medium** (workaround possible): optional artifacts missing, non-critical validation failures
- **Low** (non-blocking): formatting issues, optional info missing

## Common Recovery Patterns

### Partial stage completion (interrupted)

1. Load the stage plan file
2. Find last `[x]` checkbox
3. Resume from next uncompleted step

### Corrupted or inconsistent `aidlc-state.md`

1. Ask user which stage they're on
2. Verify against actual artifacts on disk
3. Rebuild state file from existing artifacts

### Missing artifacts from prior stage

1. Identify which stage produced them
2. If stage marked complete → re-execute that stage
3. If cannot regenerate → ask user to provide info manually
4. Document gap in `audit.md`

### User wants to restart a stage

1. Confirm (existing work will be archived)
2. Archive: `{artifact}.backup.{timestamp}`
3. Reset stage in `aidlc-state.md`
4. Re-execute from beginning

### User wants to skip a stage

1. Warn about downstream impact
2. Get explicit confirmation
3. Mark as "SKIPPED" in `aidlc-state.md`
4. Log reason in `audit.md`

## Escalation

Ask the user immediately for:
- Contradictory or ambiguous input
- Decisions requiring business judgment
- Technical constraints the agent cannot resolve

Suggest starting over if:
- Multiple stages have errors and state is severely corrupted
- Requirements have changed so much that existing artifacts are invalid

## Logging Format

```markdown
## Error - [Stage Name]
**Timestamp**: [ISO 8601]
**Severity**: [Critical/High/Medium/Low]
**Description**: [What went wrong]
**Resolution**: [How it was resolved]

---
```
