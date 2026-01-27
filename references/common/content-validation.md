# Content Validation

## Overview

Content validation ensures quality and consistency of all AI-DLC artifacts throughout the workflow.

## Validation Categories

### 1. Plan Validation

Before executing any plan, validate:

- [ ] All steps are numbered sequentially
- [ ] All steps have checkboxes [ ]
- [ ] Steps are actionable and specific
- [ ] Dependencies between steps are clear
- [ ] Output artifacts are defined

### 2. Artifact Validation

For generated artifacts, validate:

- [ ] File is saved to correct location
- [ ] Content follows expected format
- [ ] References to other artifacts are valid
- [ ] No placeholder content remains
- [ ] Traceability links are present

### 3. Code Validation

For generated code, validate:

- [ ] Code is in correct location (never aidlc-docs/)
- [ ] No duplicate files created (brownfield)
- [ ] Follows project conventions
- [ ] Includes appropriate comments
- [ ] Tests are included

### 4. State Validation

For workflow state, validate:

- [ ] aidlc-state.md is up to date
- [ ] Current phase and stage are correct
- [ ] Completed stages are marked
- [ ] Next steps are clear

## Validation Checkpoints

### Before Stage Execution

1. Verify prerequisites are met
2. Verify required artifacts exist
3. Verify state is consistent

### After Step Completion

1. Verify step output is correct
2. Update checkbox to [x]
3. Update state file

### After Stage Completion

1. Verify all steps completed
2. Verify all artifacts generated
3. Update state file
4. Log completion in audit

## Error Handling

### Missing Prerequisites

```markdown
⚠️ **Prerequisite Check Failed**

The following prerequisites are not met:
- [List missing prerequisites]

Please complete the following before proceeding:
- [Required actions]
```

### Invalid Artifact

```markdown
⚠️ **Artifact Validation Failed**

The following issues were found:
- [List issues]

Corrective actions:
- [Required fixes]
```

### State Inconsistency

```markdown
⚠️ **State Inconsistency Detected**

Current state does not match expected state:
- Expected: [expected state]
- Actual: [actual state]

Recommended action:
- [Recovery steps]
```

## Quality Checks

### Documentation Quality

- Clear and concise language
- Proper markdown formatting
- Consistent terminology
- Complete information

### Code Quality

- Follows coding standards
- Proper error handling
- Appropriate logging
- Test coverage

### Traceability

- Requirements linked to design
- Design linked to code
- Tests linked to requirements

## Validation Commands

### Manual Validation Trigger

User can request validation at any time:
- "Validate current state"
- "Check artifact quality"
- "Verify prerequisites"

### Automatic Validation

Validation runs automatically:
- Before stage execution
- After step completion
- Before user approval prompts
