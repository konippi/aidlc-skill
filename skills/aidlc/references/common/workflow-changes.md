# Mid-Workflow Changes and Phase Management

## Overview

Users may request changes to the execution plan or phase execution during the workflow. This document provides guidance on handling these requests safely and effectively.

---

## Types of Mid-Workflow Changes

### 1. Adding a Skipped Phase

**Scenario**: User wants to add a phase that was originally skipped

**Example**: "Actually, I want to add user stories even though we skipped that stage"

**Handling**:
1. **Confirm Request**: "You want to add User Stories stage. This will create user stories and personas. Confirm?"
2. **Check Dependencies**: Verify all prerequisite phases are complete
3. **Update Execution Plan**: Add phase to `workflow-plan.md` with rationale
4. **Update State**: Mark phase as "PENDING" in `aidlc-state.md`
5. **Execute Phase**: Follow normal phase execution process
6. **Log Change**: Document in `audit.md` with timestamp and reason

**Considerations**:
- May need to update later phases that could benefit from new artifacts
- Existing artifacts may need revision to incorporate new information
- Timeline will be extended

---

### 2. Skipping a Planned Phase

**Scenario**: User wants to skip a phase that was planned to execute

**Example**: "Let's skip the NFR Design stage for now"

**Handling**:
1. **Confirm Request**: "You want to skip NFR Design. This means no NFR patterns will be incorporated. Confirm?"
2. **Warn About Impact**: Explain what will be missing and potential consequences
3. **Get Explicit Confirmation**: User must explicitly confirm understanding of impact
4. **Update Execution Plan**: Mark phase as "SKIPPED" with reason
5. **Update State**: Mark phase as "SKIPPED" in `aidlc-state.md`
6. **Adjust Later Phases**: Note that later phases may need manual setup
7. **Log Change**: Document in `audit.md` with timestamp and reason


---

### 3. Restarting Current Stage

**Scenario**: User is unhappy with current stage results and wants to redo it

**Example**: "I don't like these user stories. Can we start over?"

**Handling**:
1. **Understand Concern**: "What specifically would you like to change about the stories?"
2. **Offer Options**:
   - **Option A**: Modify existing artifacts (faster, preserves some work)
   - **Option B**: Complete restart (clean slate, more time)
3. **If Restart Chosen**:
   - Archive existing artifacts: `{artifact}.backup.{timestamp}`
   - Reset stage checkboxes in plan file
   - Mark stage as "IN PROGRESS" in `aidlc-state.md`
   - Clear stage completion status
   - Re-execute from beginning
4. **Log Change**: Document reason for restart and what will change

---

### 4. Restarting Previous Stage

**Scenario**: User wants to go back and redo a completed stage

**Example**: "I want to change the architectural decision we made earlier"

**Handling**:
1. **Assess Impact**: Identify all stages that depend on the stage to be restarted
2. **Warn User**: "Restarting Application Design will require redoing: Units Generation, per-unit design, Code Generation. Confirm?"
3. **Get Explicit Confirmation**: User must understand full impact
4. **If Confirmed**:
   - Archive all affected artifacts
   - Reset all affected stages in `aidlc-state.md`
   - Clear checkboxes in all affected plan files
   - Return to the stage to restart
   - Re-execute from that point forward
5. **Log Change**: Document full impact and reason for restart

---

### 5. Changing Stage Depth

**Scenario**: User wants to change the depth level of current or upcoming stage

**Example**: "Let's do a comprehensive requirements analysis instead of standard"

**Handling**:
1. **Confirm Request**: "You want to change Requirements Analysis from Standard to Comprehensive depth. This will be more thorough but take longer. Confirm?"
2. **Update Execution Plan**: Change depth level in `workflow-plan.md`
3. **Adjust Approach**: Follow comprehensive depth guidelines for the stage
4. **Update Estimates**: Inform user of new timeline estimate
5. **Log Change**: Document depth change and reason

---

### 6. Pausing Workflow

**Scenario**: User needs to pause and resume later

**Example**: "I need to stop for now and continue tomorrow"

**Handling**:
1. **Complete Current Step**: Finish the current step in progress if possible
2. **Update Checkboxes**: Mark all completed steps with [x]
3. **Update State**: Ensure `aidlc-state.md` reflects current status
4. **Log Pause**: Document pause point in `audit.md`
5. **Provide Resume Instructions**: "When you return, I'll detect your existing project and offer to continue from: [current phase, current step]"

**On Resume**:
1. **Detect Existing Project**: Check for `aidlc-state.md`
2. **Load Context**: Read all artifacts from completed stages
3. **Show Status**: Display current stage and next step
4. **Offer Options**: Continue where left off or review previous work
5. **Log Resume**: Document resume point in `audit.md`


---

### 7. Changing Architectural Decision

**Scenario**: User wants to change from monolith to microservices (or vice versa)

**Example**: "Actually, let's do microservices instead of a monolith"

**Handling**:
1. **Assess Current Progress**: Determine how far into workflow
2. **Explain Impact**: 
   - If before Units Generation: Minimal impact, just update decision
   - If after Units Generation: Must redo Units Generation, all per-unit design
   - If after Code Generation: Significant rework required
3. **Recommend Approach**:
   - Early in workflow: Restart from Application Design stage
   - Late in workflow: Consider if modification is feasible vs. restart
4. **Get Confirmation**: User must understand full scope of change
5. **Execute Change**: Follow restart procedures for affected stages

---

### 8. Adding/Removing Units

**Scenario**: User wants to add or remove units after Units Generation

**Example**: "We need to split the Payment unit into Payment and Billing"

**Handling**:
1. **Assess Impact**: Determine which units have completed design/code
2. **Explain Consequences**:
   - Adding unit: Need to do full design and code for new unit
   - Removing unit: Need to redistribute functionality to other units
   - Splitting unit: Need to redo design and code for both resulting units
3. **Update Unit Artifacts**:
   - Modify `unit-of-work.md`
   - Update `unit-of-work-dependency.md`
   - Revise `unit-of-work-story-map.md`
4. **Reset Affected Units**: Mark affected units as needing redesign
5. **Execute Changes**: Follow normal unit design and code process for affected units

---

## General Guidelines for Handling Changes

### Before Making Changes

1. **Understand the Request**: Ask clarifying questions about what user wants to change and why
2. **Assess Impact**: Identify all affected stages, artifacts, and dependencies
3. **Explain Consequences**: Clearly communicate what will need to be redone and timeline impact
4. **Offer Alternatives**: Sometimes modification is better than restart
5. **Get Explicit Confirmation**: User must understand and accept the impact

### During Changes

1. **Archive Existing Work**: Always backup before making destructive changes
2. **Update All Tracking**: Keep `aidlc-state.md`, plan files, and `audit.md` in sync
3. **Communicate Progress**: Keep user informed about what's happening
4. **Validate Changes**: Ensure changes are consistent across all artifacts
5. **Test Continuity**: Verify workflow can continue smoothly after changes

### After Changes

1. **Verify Consistency**: Check that all artifacts are aligned with changes
2. **Update Documentation**: Ensure all references are updated
3. **Log Completely**: Document full change history in `audit.md`
4. **Confirm with User**: Verify changes meet user's expectations
5. **Resume Workflow**: Continue with normal execution from new state

---

## Critical Rules

1. **ALWAYS Confirm**: Never make destructive changes without explicit user confirmation
2. **ALWAYS Explain Impact**: Users need to understand consequences before deciding
3. **ALWAYS Offer Options**: Sometimes there are multiple ways to handle a change
4. **ALWAYS Archive First**: Always backup before making destructive changes
5. **ALWAYS Update Everything**: Keep all tracking files in sync
6. **ALWAYS Log Thoroughly**: Document all changes for audit trail
7. **ALWAYS Validate After**: Ensure workflow can continue smoothly
8. **BE Flexible**: Workflow should adapt to user needs, not force rigid process
