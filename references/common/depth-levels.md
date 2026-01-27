# Depth Levels

## Overview

AI-DLC uses adaptive depth levels to tailor the workflow intensity based on project complexity and risk.

## Three Depth Levels

### 🟢 Minimal Depth

**When to Use**:
- Clear, simple request
- Low risk changes
- Well-understood domain
- Single component changes
- Bug fixes with clear scope

**Characteristics**:
- Document intent only
- Skip optional stages
- Minimal questions
- Fast execution

**Stages Typically Executed**:
- Workspace Detection (ALWAYS)
- Requirements Analysis (brief)
- Workflow Planning (simple)
- Code Generation (ALWAYS)
- Build and Test (ALWAYS)

**Example Triggers**:
- "Add a simple validation"
- "Fix this bug"
- "Update this configuration"

---

### 🟡 Standard Depth

**When to Use**:
- Normal complexity
- Moderate risk
- New features with clear requirements
- Multiple component changes
- Integration work

**Characteristics**:
- Gather functional and non-functional requirements
- Execute conditional stages as needed
- Standard question depth
- Balanced execution

**Stages Typically Executed**:
- Workspace Detection (ALWAYS)
- Requirements Analysis (standard)
- User Stories (if user-facing)
- Workflow Planning (ALWAYS)
- Application Design (if new components)
- Units Generation (if multiple units)
- Functional Design (per unit)
- NFR Requirements (per unit)
- Code Generation (ALWAYS)
- Build and Test (ALWAYS)

**Example Triggers**:
- "Build a new API endpoint"
- "Add user authentication"
- "Create a new service"

---

### 🔴 Comprehensive Depth

**When to Use**:
- Complex, high-risk changes
- Critical business functionality
- Multiple stakeholders
- Regulatory/compliance requirements
- Large-scale refactoring
- New system architecture

**Characteristics**:
- Detailed requirements with traceability
- Execute all relevant stages
- Comprehensive questions
- Thorough documentation

**Stages Typically Executed**:
- Workspace Detection (ALWAYS)
- Reverse Engineering (if brownfield)
- Requirements Analysis (comprehensive)
- User Stories (detailed personas)
- Workflow Planning (ALWAYS)
- Application Design (detailed)
- Units Generation (detailed)
- Functional Design (per unit)
- NFR Requirements (per unit)
- NFR Design (per unit)
- Infrastructure Design (per unit)
- Code Generation (ALWAYS)
- Build and Test (ALWAYS)

**Example Triggers**:
- "Design a new microservices architecture"
- "Build a payment processing system"
- "Implement GDPR compliance features"

---

## Depth Selection

### Automatic Detection

AI-DLC analyzes the request to suggest appropriate depth:

| Signal | Suggested Depth |
|--------|-----------------|
| "simple", "quick", "just" | Minimal |
| "new feature", "add", "create" | Standard |
| "architecture", "system", "critical" | Comprehensive |
| Multiple components mentioned | Standard or Comprehensive |
| Security/compliance mentioned | Comprehensive |
| Bug fix, config change | Minimal |

### User Override

User can always override the suggested depth:
- "Use minimal depth"
- "Use comprehensive depth"
- "Skip [stage name]"
- "Include [stage name]"

### Depth Confirmation

Always confirm depth with user:

```markdown
Based on your request, I recommend **[Standard]** depth.

This will include:
- [List of stages]

Would you like to:
- Proceed with Standard depth
- Use Minimal depth (faster, less documentation)
- Use Comprehensive depth (more thorough)
```

## Depth Impact on Questions

### Minimal Depth Questions

```markdown
**Q1**: What is the main goal?
[Answer]: 

**Q2**: Any constraints I should know about?
[Answer]: 
```

### Standard Depth Questions

```markdown
### Functional Requirements

**Q1**: What is the primary purpose?
[Answer]: 

**Q2**: Who are the target users?
[Answer]: 

### Technical Requirements

**Q3**: Any technology preferences?
[Answer]: 

**Q4**: What integrations are needed?
[Answer]: 
```

### Comprehensive Depth Questions

```markdown
### Business Context

**Q1**: What business problem does this solve?
[Answer]: 

**Q2**: Who are the stakeholders?
[Answer]: 

**Q3**: What are the success metrics?
[Answer]: 

### Functional Requirements

**Q4**: What are the core features?
[Answer]: 

**Q5**: What are the edge cases?
[Answer]: 

### Non-Functional Requirements

**Q6**: What are the performance requirements?
[Answer]: 

**Q7**: What are the security requirements?
[Answer]: 

**Q8**: What are the compliance requirements?
[Answer]: 

### Technical Context

**Q9**: What is the current architecture?
[Answer]: 

**Q10**: What are the integration points?
[Answer]: 
```

## Critical Rules

1. **ALWAYS confirm depth** with user before proceeding
2. **ALLOW user override** at any time
3. **ADJUST dynamically** if complexity changes during execution
4. **DOCUMENT depth choice** in aidlc-state.md
