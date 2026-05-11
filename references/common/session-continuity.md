# Session Continuity Templates

## Welcome Back Prompt Template
When a user returns to continue work on an existing AI-DLC project, present this prompt:

```markdown
**Welcome back! I can see you have an existing AI-DLC project in progress.**

Based on your aidlc-state.md, here's your current status:
- **Project**: [project-name]
- **Current Phase**: [INCEPTION/CONSTRUCTION/OPERATIONS]
- **Current Stage**: [Stage Name]
- **Last Completed**: [Last completed step]
- **Next Step**: [Next step to work on]

**What would you like to work on today?**

A) Continue where you left off ([Next step description])
B) Review a previous stage ([Show available stages])

[Answer]: 
```

## MANDATORY: Session Continuity Instructions
1. **Always read aidlc-state.md first** when detecting existing project
2. **Verify approval status** — cross-check `aidlc-state.md` against `audit.md`. If the current stage shows `waiting-approval` or if `audit.md` has no approval record for the last completed stage, halt at the approval gate rather than proceeding. Never assume `COMPLETED` means approved without audit confirmation.
3. **Parse current status** from the workflow file to populate the prompt
3. **MANDATORY: Load Previous Stage Artifacts** - Before resuming any stage, automatically read all relevant artifacts from completed stages. Scan these directories for all `.md` files:
   - **Reverse Engineering**: `aidlc-docs/inception/reverse-engineering/` (all files)
   - **Requirements Analysis**: `aidlc-docs/inception/requirements/` (all files)
   - **User Stories**: `aidlc-docs/inception/user-stories/` (all files)
   - **Application Design**: `aidlc-docs/inception/application-design/` (all files)
   - **Per-Unit Design**: `aidlc-docs/construction/{unit-name}/` (all subdirectories)
   - **Code Stages**: All above + existing code files in workspace root
4. **Smart Context Loading by Stage**:
   - **Early Stages (Workspace Detection, Reverse Engineering)**: Load workspace analysis
   - **Requirements/Stories**: Load reverse engineering + requirements artifacts
   - **Design Stages**: Load requirements + stories + architecture + design artifacts
   - **Code Stages**: Load ALL artifacts + existing code files
5. **Adapt options** based on architectural choice and current phase
6. **Show specific next steps** rather than generic descriptions
7. **Log the continuity prompt** in audit.md with timestamp
8. **Context Summary**: After loading artifacts, provide brief summary of what was loaded for user awareness

## Error Handling
If artifacts are missing or corrupted during session resumption, see [error-handling.md](error-handling.md) for recovery procedures.