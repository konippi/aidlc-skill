# Content Validation Rules

All generated content MUST be validated before writing to files.

## Diagrams

Prefer Mermaid. For simple layouts (directory trees, box-and-arrow), basic ASCII (`+` `-` `|` spaces) is acceptable — ensure all box lines have identical character width. No Unicode box-drawing characters (`┌` `─` `│` `└` `├` etc.).

### Mermaid Validation

Before writing any Mermaid diagram:

1. Node IDs: alphanumeric + underscore only
2. Escape special characters in labels (`"` → `\"`)
3. Validate syntax (valid node connections)
4. If validation fails, use a text-based list as fallback

## General Validation

Before writing any file:

1. Validate embedded code blocks (Mermaid, JSON, YAML)
2. Check special character escaping
3. Verify markdown syntax correctness
4. Include text fallback for complex visual elements

## On Failure

1. Log what failed in `audit.md`
2. Use text-based fallback
3. Continue workflow (don't block)
4. Inform user that simplified content was used
