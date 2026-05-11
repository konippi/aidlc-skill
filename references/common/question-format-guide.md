# Question Format Guide

## Rule: Never Ask Questions in Chat

ALL questions MUST be placed in dedicated question files. Never ask questions inline in the conversation.

## File Format

File name: `aidlc-docs/inception/requirements/requirement-verification-questions.md` (or `{phase}-questions.md` for other phases).

Question structure:

```markdown
## Question [Number]

[Clear, specific question text]

A) [First option]

B) [Second option]

C) [Third option if needed]

X) Other (please describe after [Answer]: tag below)

[Answer]:
```

**Important**: Separate each option with a blank line so strict CommonMark renderers display them as distinct lines.

## Rules

- "Other" (X) is MANDATORY as the last option for every question
- Minimum 2 meaningful options + Other
- Options must be mutually exclusive
- Only include meaningful options — do not pad to fill A-E slots
- User responds by writing a **single** letter after `[Answer]:` — if multiple letters are provided, ask the user to pick one (options are mutually exclusive)

## Reading Responses

1. Read the question file
2. Extract answers after `[Answer]:` tags
3. Validate all questions are answered
4. Check for contradictions between answers (see below)
5. Proceed with analysis

## Contradiction and Ambiguity Detection

After reading responses, check for logically inconsistent answers:

- Scope vs impact mismatch (e.g., "bug fix" but "entire codebase affected")
- Risk vs change type mismatch (e.g., "low risk" but "breaking changes")

If contradictions found:

1. Create `{phase}-clarification-questions.md`
2. State which answers conflict and why
3. Ask targeted multiple-choice questions to resolve
4. Do NOT proceed until all contradictions are resolved

## Error Handling

- Missing answer → ask user to complete unanswered questions
- Invalid answer (not a letter choice) → ask user to use letter format
- Ambiguous answer → ask user to pick a letter or choose X (Other)
