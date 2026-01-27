# Requirements Analysis - Detailed Steps

## Overview

Analyze user request and generate requirements document. This stage ALWAYS executes but depth varies based on request clarity and complexity.

## Prerequisites

- Workspace Detection must be complete
- Reverse Engineering must be complete (if brownfield)

## Execution Steps

### Step 1: Load Reverse Engineering Context (if available)

**IF brownfield project**:
- Load `aidlc-docs/inception/reverse-engineering/architecture.md`
- Load `aidlc-docs/inception/reverse-engineering/component-inventory.md`
- Load `aidlc-docs/inception/reverse-engineering/technology-stack.md`
- Use these to understand existing system when analyzing request

### Step 2: Analyze User Request (Intent Analysis)

#### 2.1 Request Clarity
- **Clear**: Specific, well-defined, actionable
- **Vague**: General, ambiguous, needs clarification
- **Incomplete**: Missing key information

#### 2.2 Request Type
- **New Feature**: Adding new functionality
- **Bug Fix**: Fixing existing issue
- **Refactoring**: Improving code structure
- **Upgrade**: Updating dependencies or frameworks
- **Migration**: Moving to different technology
- **Enhancement**: Improving existing feature
- **New Project**: Starting from scratch

#### 2.3 Initial Scope Estimate
- **Single File**: Changes to one file
- **Single Component**: Changes to one component/package
- **Multiple Components**: Changes across multiple components
- **System-wide**: Changes affecting entire system
- **Cross-system**: Changes affecting multiple systems

#### 2.4 Initial Complexity Estimate
- **Trivial**: Simple, straightforward change
- **Simple**: Clear implementation path
- **Moderate**: Some complexity, multiple considerations
- **Complex**: Significant complexity, many considerations

### Step 3: Determine Requirements Depth

| Depth | Criteria |
|-------|----------|
| Minimal | Request is clear and simple, no detailed requirements needed |
| Standard | Request needs clarification, functional and non-functional requirements needed |
| Comprehensive | Complex project, high risk, detailed requirements with traceability needed |


### Step 4: Assess Current Requirements

Analyze whatever the user has provided:
- Intent statements or descriptions
- Existing requirements documents
- Pasted content or file references
- Convert any non-markdown documents to markdown format

### Step 5: Thorough Completeness Analysis

**CRITICAL**: Use comprehensive analysis to evaluate requirements completeness. Default to asking questions when there is ANY ambiguity or missing detail. Focus on WHAT needs to be achieved and WHY, NOT HOW to implement it.

**MANDATORY**: Evaluate ALL of these areas and ask questions for ANY that are unclear:
- **Functional Requirements**: Core features, user interactions, system behaviors
- **Non-Functional Requirements**: Performance, security, scalability, usability
- **User Scenarios**: Use cases, user journeys, edge cases, error scenarios
- **Business Context**: Goals, constraints, success criteria, stakeholder needs
- **Technical Context**: Integration points, data requirements, system boundaries
- **Quality Attributes**: Reliability, maintainability, testability, accessibility

### Step 6: Generate Clarifying Questions

**ALWAYS** create `aidlc-docs/inception/requirements/requirement-verification-questions.md` unless requirements are exceptionally clear and complete.

**Question Format** (see `question-format-guide.md`):
```markdown
### Q1: [Question content]

A) Option 1
B) Option 2
C) Option 3
X) Other (please describe after [Answer]: tag below)

[Answer]: 
```

- Focus on ambiguities and missing information
- Generate questions only where user input is needed
- Wait for user to fill in all [Answer]: tags

### Step 7: Analyze Answers for Ambiguities

**MANDATORY**: Before proceeding, carefully review all user answers for:
- **Vague responses**: "mix of", "somewhere between", "not sure", "depends"
- **Undefined criteria or terms**: References to concepts without clear definitions
- **Contradictory answers**: Responses that conflict with each other
- **Missing generation details**: Answers that lack specific guidance
- **Answers that combine options**: Responses that merge different approaches without clear decision rules

### Step 8: Create Follow-up Questions (if needed)

If analysis reveals ANY ambiguous answers:
- Add specific follow-up questions using [Answer]: tags
- **DO NOT proceed to approval until all ambiguities are resolved**

### Step 9: Generate Requirements Document

Create `aidlc-docs/inception/requirements/requirements.md` including:
- Intent analysis summary at the top
- User request
- Request type
- Scope estimate
- Complexity estimate
- Functional requirements
- Non-functional requirements
- User's answers incorporated

### Step 10: Update State Tracking

Update `aidlc-docs/aidlc-state.md`:
```markdown
## Stage Progress
### 🔵 INCEPTION PHASE
- [x] Workspace Detection
- [x] Reverse Engineering (if applicable)
- [x] Requirements Analysis
```

### Step 11: Log and Present Completion

Log approval prompt in `aidlc-docs/audit.md`, then present:

```markdown
# 🔍 Requirements Analysis Complete

[AI-generated summary of requirements in bullet points]

> **📋 REVIEW REQUIRED:**  
> Please examine the requirements document at: `aidlc-docs/inception/requirements/requirements.md`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the requirements
> 📝 **Add User Stories** - Include User Stories stage (if currently skipped)
> ✅ **Approve & Continue** - Approve requirements and proceed to **[User Stories/Workflow Planning]**
```

### Step 12: Wait for Explicit Approval

- **DO NOT proceed until user explicitly approves**
- Record approval response with timestamp in audit.md
- Update Requirements Analysis stage complete in aidlc-state.md

## Critical Rules

- **ALWAYS** create questions file unless requirements are exceptionally clear
- **NEVER** proceed with ambiguous answers - resolve ALL ambiguities first
- **ALWAYS** wait for explicit approval before next stage
- **ALWAYS** log all interactions in audit.md
