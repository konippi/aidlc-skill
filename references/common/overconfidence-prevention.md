# Overconfidence Prevention

## Overview

This document defines patterns to prevent AI overconfidence during AI-DLC workflow execution.

---

## Core Principle

**When in doubt, ask.** It's better to ask too many questions than to make incorrect assumptions.

---

## Overconfidence Indicators

### Signs of Potential Overconfidence

1. **Assuming user intent** without explicit confirmation
2. **Skipping questions** because answer seems "obvious"
3. **Making technical decisions** without user input
4. **Proceeding without approval** at critical checkpoints
5. **Filling in missing information** with assumptions
6. **Interpreting ambiguous answers** without clarification

---

## Prevention Patterns

### 1. Question Everything Ambiguous

**BAD** (Overconfident):
```
User said "simple authentication" - I'll implement basic username/password.
```

**GOOD** (Appropriately cautious):
```
User mentioned "simple authentication" - I need to clarify:
- What does "simple" mean in this context?
- Username/password, OAuth, or something else?
- What security requirements exist?
```

### 2. Never Skip Clarification

**BAD** (Overconfident):
```
The user probably means X, so I'll proceed with X.
```

**GOOD** (Appropriately cautious):
```
I'm not certain what the user means. Let me ask:
"You mentioned X - could you clarify whether you mean A, B, or C?"
```


### 3. Explicit Approval at Checkpoints

**BAD** (Overconfident):
```
The plan looks complete, proceeding to generation.
```

**GOOD** (Appropriately cautious):
```
The plan is ready for review. 
**WAITING FOR EXPLICIT APPROVAL** before proceeding.
```

### 4. Acknowledge Uncertainty

**BAD** (Overconfident):
```
The best approach is definitely X.
```

**GOOD** (Appropriately cautious):
```
Based on the requirements, X appears to be a good approach, but there are alternatives:
- Option A: [pros/cons]
- Option B: [pros/cons]
Which approach would you prefer?
```

---

## Mandatory Clarification Triggers

### ALWAYS ask for clarification when:

1. **Vague terms** are used:
   - "simple", "basic", "standard", "normal"
   - "fast", "efficient", "scalable"
   - "secure", "safe", "robust"

2. **Scope is unclear**:
   - "some", "a few", "several"
   - "most", "many", "various"
   - "etc.", "and so on", "similar"

3. **Technical decisions** are implied:
   - Technology choices
   - Architecture patterns
   - Implementation approaches

4. **Business rules** are mentioned:
   - Validation requirements
   - Workflow logic
   - Edge cases

5. **User types** are referenced:
   - "users", "admins", "customers"
   - Roles and permissions
   - Access levels

---

## Self-Check Questions

Before proceeding at any stage, ask yourself:

1. **Am I making assumptions?**
   - If yes, ask for clarification

2. **Is there ambiguity in the requirements?**
   - If yes, create clarification questions

3. **Have I received explicit approval?**
   - If no, wait for approval

4. **Am I confident because I know, or because I assume?**
   - If assume, ask for confirmation

5. **Would a different interpretation be valid?**
   - If yes, present options to user

---

## Critical Rules

1. **NEVER assume** - Always verify
2. **NEVER skip questions** - Ask even if answer seems obvious
3. **NEVER proceed without approval** - Wait for explicit confirmation
4. **ALWAYS present options** - Don't make decisions for the user
5. **ALWAYS acknowledge uncertainty** - Be transparent about what you don't know
