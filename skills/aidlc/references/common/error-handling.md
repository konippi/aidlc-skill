# Error Handling

## Overview

This document defines error handling patterns for AI-DLC workflow execution.

---

## Error Categories

### 1. File System Errors

#### File Not Found
```markdown
⚠️ **File Not Found Error**

The required file was not found:
- **Expected**: `[file path]`
- **Context**: [What operation was being performed]

**Recovery Options**:
A) Create the missing file
B) Skip this step and continue
C) Return to previous stage
D) Abort workflow

[Answer]: 
```

#### Permission Denied
```markdown
⚠️ **Permission Denied Error**

Unable to access file:
- **File**: `[file path]`
- **Operation**: [read/write/delete]

**Recovery Options**:
A) Retry with different permissions
B) Use alternative location
C) Skip this operation
D) Abort workflow

[Answer]: 
```


### 2. Validation Errors

#### Missing Prerequisites
```markdown
⚠️ **Prerequisite Check Failed**

The following prerequisites are not met:
- [List missing prerequisites]

**Required Actions**:
- [List what needs to be completed]

**Recovery Options**:
A) Complete missing prerequisites now
B) Skip prerequisite check and proceed (not recommended)
C) Return to previous stage
D) Abort workflow

[Answer]: 
```

#### Invalid Content
```markdown
⚠️ **Content Validation Failed**

The following issues were found:
- [List validation issues]

**Recovery Options**:
A) Auto-fix issues
B) Manual review and fix
C) Skip validation
D) Abort workflow

[Answer]: 
```

### 3. State Errors

#### State Inconsistency
```markdown
⚠️ **State Inconsistency Detected**

Current state does not match expected state:
- **Expected**: [expected state]
- **Actual**: [actual state]

**Recovery Options**:
A) Auto-repair state based on audit trail
B) Manual state correction
C) Reset to last known good state
D) Abort workflow

[Answer]: 
```

#### Missing State File
```markdown
⚠️ **State File Missing**

The workflow state file was not found:
- **Expected**: `aidlc-docs/aidlc-state.md`

**Recovery Options**:
A) Create new state file (start fresh)
B) Attempt recovery from audit trail
C) Abort workflow

[Answer]: 
```


### 4. User Input Errors

#### Missing Answers
```markdown
⚠️ **Incomplete User Input**

The following questions were not answered:
- Question [X]: [question text]
- Question [Y]: [question text]

**Required Action**:
Please provide answers for all questions before proceeding.
```

#### Invalid Answer Format
```markdown
⚠️ **Invalid Answer Format**

Question [X] has an invalid answer:
- **Provided**: "[user's answer]"
- **Expected**: Letter choice (A, B, C, etc.)

**Required Action**:
Please provide a valid letter choice for this question.
```

### 5. Generation Errors

#### Code Generation Failed
```markdown
⚠️ **Code Generation Error**

Failed to generate code:
- **Step**: [step number and description]
- **Error**: [error details]

**Recovery Options**:
A) Retry generation
B) Skip this step
C) Manual intervention required
D) Abort code generation

[Answer]: 
```

#### Artifact Creation Failed
```markdown
⚠️ **Artifact Creation Error**

Failed to create artifact:
- **Artifact**: `[artifact path]`
- **Error**: [error details]

**Recovery Options**:
A) Retry creation
B) Create in alternative location
C) Skip artifact
D) Abort workflow

[Answer]: 
```

---

## Error Recovery Patterns

### Automatic Recovery

For recoverable errors, attempt automatic recovery:

1. **Retry with backoff**: Retry operation up to 3 times with increasing delays
2. **Alternative path**: Try alternative approach if primary fails
3. **Graceful degradation**: Continue with reduced functionality

### Manual Recovery

For non-recoverable errors, request user intervention:

1. **Clear explanation**: Explain what went wrong
2. **Options**: Provide clear recovery options
3. **Guidance**: Recommend best recovery path
4. **Logging**: Log error and recovery action in audit trail


---

## Error Logging

All errors must be logged in `aidlc-docs/audit.md`:

```markdown
## Error Log Entry
**Timestamp**: [ISO 8601 timestamp]
**Error Type**: [Category]
**Error Message**: [Detailed error message]
**Context**: [What was being done when error occurred]
**Recovery Action**: [What action was taken]
**Outcome**: [Success/Failure of recovery]

---
```

---

## Critical Rules

1. **NEVER silently fail** - Always inform user of errors
2. **ALWAYS log errors** - Maintain complete error history
3. **ALWAYS offer recovery options** - Don't leave user stuck
4. **NEVER lose user work** - Preserve state before risky operations
5. **ALWAYS explain clearly** - User should understand what went wrong
