# Adaptive Depth

## Core Principle

**When a stage executes, ALL its defined artifacts are created. The "depth" refers to the level of detail and rigor within those artifacts, which adapts to the problem's complexity.**

## Stage Selection vs Detail Level

- **Stage Selection** (binary): Workflow Planning decides EXECUTE or SKIP for each stage
- **Detail Level** (adaptive): Simple problems get concise artifacts; complex problems get comprehensive artifacts. The model decides based on problem characteristics.

## Factors Influencing Detail Level

1. **Request Clarity**: How clear and complete is the user's request?
2. **Problem Complexity**: How intricate is the solution space?
3. **Scope**: Single file, component, multiple components, or system-wide?
4. **Risk Level**: What's the impact of errors or omissions?
5. **Available Context**: Greenfield vs brownfield, existing documentation
6. **User Preferences**: Has user expressed preference for brevity or detail?

## Example: Requirements Analysis

**All scenarios create the same artifacts** (`requirement-verification-questions.md`, `requirements.md`). Detail level varies:

- **Simple** (bug fix): Few clarifying questions, concise functional requirement
- **Complex** (system migration): Multiple question rounds (10+), comprehensive functional + non-functional requirements with traceability

## Guiding Principle

**"Create exactly the detail needed for the problem at hand — no more, no less."**

- Don't inflate simple problems with unnecessary detail
- Don't shortchange complex problems by omitting critical detail
- All required artifacts are always created when a stage executes
