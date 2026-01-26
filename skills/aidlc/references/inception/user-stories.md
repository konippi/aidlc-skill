# User Stories - Detailed Steps

## Purpose
**Convert requirements into user-centered stories with acceptance criteria**

User Stories focus on:
- Translating business requirements into user-centered narratives
- Defining clear acceptance criteria for each story
- Creating user personas that represent different stakeholder types
- Establishing shared understanding across teams
- Providing testable specifications for implementation

## Prerequisites

- Workspace Detection must be complete
- Requirements Analysis recommended (can reference requirements if available)
- Workflow Planning must indicate User Stories stage should execute

## Intelligent Assessment Guidelines

**WHEN TO EXECUTE USER STORIES**: Use this enhanced assessment before proceeding:

### High Priority Execution (ALWAYS Execute)
- **New User Features**: Any new functionality users will directly interact with
- **User Experience Changes**: Modifications to existing user workflows or interfaces
- **Multi-Persona Systems**: Applications serving different types of users
- **Customer-Facing APIs**: Services that external users or systems will consume
- **Complex Business Logic**: Requirements with multiple scenarios or business rules
- **Cross-Team Projects**: Work requiring shared understanding across multiple teams

### Medium Priority Execution (Assess Complexity)
- **Backend User Impact**: Internal changes that indirectly affect user experience
- **Performance Improvements**: Enhancements with user-visible benefits
- **Integration Work**: Connecting systems that affect user workflows
- **Data Changes**: Modifications affecting user data, reports, or analytics
- **Security Enhancements**: Changes affecting user authentication or permissions

### Skip Only For Simple Cases
- **Pure Refactoring**: Internal code improvements with zero user impact
- **Isolated Bug Fixes**: Simple, well-defined fixes with clear scope
- **Infrastructure Only**: Changes with no user-facing effects
- **Developer Tooling**: Build processes, CI/CD, or development environment changes
- **Documentation**: Updates that don't affect functionality

---

# PART 1: PLANNING

## Step 1: Validate User Stories Need (MANDATORY)

Create `aidlc-docs/inception/plans/user-stories-assessment.md`:
```markdown
# User Stories Assessment

## Request Analysis
- **Original Request**: [Brief summary]
- **User Impact**: [Direct/Indirect/None]
- **Complexity Level**: [Simple/Medium/Complex]
- **Stakeholders**: [List involved parties]

## Assessment Criteria Met
- [ ] High Priority: [List applicable criteria]
- [ ] Medium Priority: [List applicable criteria]
- [ ] Benefits: [Expected value from user stories]

## Decision
**Execute User Stories**: [Yes/No]
**Reasoning**: [Detailed justification]
```


## Step 2: Create Story Plan

Generate a comprehensive plan with step-by-step execution checklist:
- Each step and sub-step should have a checkbox [ ]
- Focus on methodology and approach for converting requirements into user stories

## Step 3: Generate Context-Appropriate Questions

**Question categories to evaluate**:
- **User Personas**: User types, roles, characteristics, motivations
- **Story Granularity**: Appropriate level of detail, story size
- **Story Format**: Format preferences, template usage
- **Breakdown Approach**: Organization method, prioritization
- **Acceptance Criteria**: Detail level, format, testing approach
- **User Journeys**: User workflows, interaction patterns

Use [Answer]: tag format for all questions.

## Step 4: Include Mandatory Story Artifacts in Plan

- [ ] Generate `aidlc-docs/inception/user-stories/stories.md` with user stories following INVEST criteria
- [ ] Generate `aidlc-docs/inception/user-stories/personas.md` with user archetypes
- [ ] Ensure stories are Independent, Negotiable, Valuable, Estimable, Small, Testable
- [ ] Include acceptance criteria for each story
- [ ] Map personas to relevant user stories

## Step 5: Store Story Plan

Save as `aidlc-docs/inception/plans/story-generation-plan.md`

## Step 6: Request User Input

Ask user to fill in all [Answer]: tags directly in the plan document.

## Step 7: Collect and Analyze Answers

Wait for user to provide answers, then analyze for:
- Vague or ambiguous responses
- Undefined criteria or terms
- Contradictory answers
- Missing generation details

## Step 8: Create Follow-up Questions (if needed)

If ANY ambiguities found, create follow-up questions. **DO NOT proceed until resolved.**

## Step 9: Wait for Plan Approval

Ask: "**Story generation plan complete. Review the plan. Ready to proceed to generation?**"

**DO NOT PROCEED until user confirms.**

---

# PART 2: GENERATION

## Step 10: Load Story Generation Plan

- Read the complete plan from `aidlc-docs/inception/plans/story-generation-plan.md`
- Identify the next uncompleted step (first [ ] checkbox)

## Step 11: Execute Current Step

- Perform exactly what the current step describes
- Generate story artifacts as specified in the plan
- Follow the approved methodology and format

## Step 12: Update Progress

- Mark the completed step as [x] in the story generation plan
- Update `aidlc-docs/aidlc-state.md` current status
- Save all generated artifacts

## Step 13: Continue or Complete

- If more steps remain, return to Step 10
- If all steps complete, proceed to completion message

## Step 14: Present Completion Message

```markdown
# 📚 User Stories Complete

[AI-generated summary of stories and personas in bullet points]

> **📋 REVIEW REQUIRED:**  
> Please examine the user stories and personas at:
> - `aidlc-docs/inception/user-stories/stories.md`
> - `aidlc-docs/inception/user-stories/personas.md`

> **🚀 WHAT'S NEXT?**
>
> **You may:**
>
> 🔧 **Request Changes** - Ask for modifications to the stories or personas
> ✅ **Approve & Continue** - Approve user stories and proceed to **Workflow Planning**
```

## Step 15: Wait for Explicit Approval

- **DO NOT proceed until user explicitly approves**
- Log approval in audit.md with timestamp
- Mark User Stories stage complete in aidlc-state.md

## Critical Rules

- **ALWAYS** perform intelligent assessment before proceeding
- **NEVER** proceed with ambiguous answers
- **ALWAYS** follow Planning → Generation pattern
- **ALWAYS** wait for explicit approval at both plan and generation stages
