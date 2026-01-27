# Build and Test - Detailed Steps

## Overview

Build all units and execute comprehensive testing through two integrated parts:
- **Part 1 - Planning**: Create build and test plan with explicit steps
- **Part 2 - Execution**: Execute approved plan to build, test, and validate all units

**Note**: This stage executes AFTER all units have completed Code Generation.

## Prerequisites

- Code Generation must be complete for ALL units
- All application code must be generated
- Test code must be generated for each unit

---

# PART 1: PLANNING

## Step 1: Analyze Build Context

- [ ] Read all unit code generation summaries
- [ ] Identify build dependencies between units
- [ ] Review technology stack for build tools
- [ ] Identify test frameworks and strategies

## Step 2: Create Build and Test Plan

- [ ] Define build order (respecting dependencies)
- [ ] Identify test categories:
  - Unit tests (per unit)
  - Integration tests (cross-unit)
  - End-to-end tests (full system)
  - Performance tests (if NFR requirements exist)
  - Security tests (if security requirements exist)
- [ ] Create explicit steps:
  - Dependency Installation
  - Code Compilation/Transpilation
  - Unit Test Execution (per unit)
  - Integration Test Execution
  - End-to-End Test Execution
  - Code Quality Checks (linting, formatting)
  - Security Scanning
  - Build Artifact Generation
- [ ] Number each step sequentially
- [ ] Add checkboxes [ ] for each step

## Step 3: Generate Context-Appropriate Questions

Generate questions using [Answer]: tag format:

```markdown
### Build Configuration

**Q1**: What build tool should be used?
[Answer]: 

**Q2**: Are there any specific build configurations needed?
[Answer]: 

### Test Configuration

**Q3**: What test coverage threshold is required?
[Answer]: 

**Q4**: Are there any tests that should be skipped initially?
[Answer]: 

### Quality Gates

**Q5**: What code quality checks should be enforced?
[Answer]: 
```

## Step 4: Collect and Analyze Answers

- [ ] Wait for user to provide answers
- [ ] Analyze answers for completeness
- [ ] Generate follow-up questions if needed

## Step 5: Create Plan Document

Save complete plan as `aidlc-docs/construction/plans/build-and-test-plan.md`

## Step 6: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**


---

# PART 2: EXECUTION

## Step 7: Load Build and Test Plan

- [ ] Read the complete plan
- [ ] Identify the next uncompleted step
- [ ] Load the context for that step

## Step 8: Execute Current Step

Execute build and test steps:

### Dependency Installation
- Install all project dependencies
- Verify dependency versions
- Check for security vulnerabilities

### Code Compilation
- Compile/transpile source code
- Generate type definitions (if applicable)
- Verify no compilation errors

### Unit Test Execution
- Run unit tests for each unit
- Collect coverage metrics
- Report test results

### Integration Test Execution
- Run integration tests
- Verify cross-unit interactions
- Test external service integrations

### End-to-End Test Execution
- Run E2E tests
- Verify complete user flows
- Test edge cases

### Code Quality Checks
- Run linter
- Check code formatting
- Run static analysis

### Security Scanning
- Run dependency vulnerability scan
- Run SAST (Static Application Security Testing)
- Check for secrets in code

### Build Artifact Generation
- Generate deployable artifacts
- Create container images (if applicable)
- Generate deployment manifests

## Step 9: Handle Test Failures

If tests fail:
- [ ] Document failing tests
- [ ] Analyze failure causes
- [ ] Present failure summary to user
- [ ] Wait for user decision (fix or proceed)

## Step 10: Update Progress

- [ ] Mark the completed step as [x] in the plan
- [ ] Update `aidlc-docs/aidlc-state.md` current status
- [ ] Save test results and reports

## Step 11: Continue or Complete

- [ ] If more steps remain, return to Step 7
- [ ] If all steps complete, proceed to completion message

## Step 12: Present Completion Message

```markdown
# ✅ Build and Test Complete

[AI-generated summary]
- Build status: [SUCCESS/FAILED]
- Unit tests: [X passed, Y failed]
- Integration tests: [X passed, Y failed]
- Code coverage: [X%]
- Quality checks: [PASSED/FAILED]

> **📋 REVIEW REQUIRED:**  
> Please examine:
> - Test results: `aidlc-docs/construction/build-and-test/test-results.md`
> - Coverage report: `aidlc-docs/construction/build-and-test/coverage.md`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Fix Issues** - Address failing tests or quality issues
> ✅ **Complete Construction** - Proceed to **Operations Phase** (or complete workflow)
```

## Step 13: Wait for Explicit Approval

- **DO NOT PROCEED until user explicitly approves**

## Step 14: Record Approval and Update Progress

- Log approval in audit.md with timestamp
- Mark Build and Test stage as complete
- Mark Construction Phase as complete

---

## Output Artifacts

- `aidlc-docs/construction/build-and-test/build-log.md`
- `aidlc-docs/construction/build-and-test/test-results.md`
- `aidlc-docs/construction/build-and-test/coverage.md`
- `aidlc-docs/construction/build-and-test/quality-report.md`
- `aidlc-docs/construction/build-and-test/security-scan.md`

## Test Result Format

```markdown
## Unit Test Results

| Unit | Tests | Passed | Failed | Coverage |
|------|-------|--------|--------|----------|
| unit-1 | 25 | 25 | 0 | 85% |
| unit-2 | 18 | 17 | 1 | 78% |

## Failed Tests

### unit-2
- `test_user_validation`: Expected validation error, got success
  - File: `tests/unit-2/test_user.py:45`
  - Cause: Missing validation rule
```

## Critical Rules

- **ALL UNITS**: Build and test ALL units, not just one
- **REPORT FAILURES**: Always report test failures clearly
- **USER DECISION**: Let user decide how to handle failures
- **EXPLICIT APPROVAL**: Never proceed without user approval
