# ASCII Diagram Standards

## Overview

This document defines standards for ASCII diagrams used in AI-DLC documentation.

---

## When to Use ASCII Diagrams

Use ASCII diagrams for:
- Architecture overviews
- Component relationships
- Data flow visualization
- Process flows
- System boundaries

---

## Basic Elements

### Boxes
```
┌─────────────────┐
│   Component     │
└─────────────────┘
```

### Arrows
```
→  Right arrow
←  Left arrow
↑  Up arrow
↓  Down arrow
↔  Bidirectional
```

### Connectors
```
├  T-junction (right)
┤  T-junction (left)
┬  T-junction (down)
┴  T-junction (up)
┼  Cross junction
```

### Corners
```
┌  Top-left corner
┐  Top-right corner
└  Bottom-left corner
┘  Bottom-right corner
```


---

## Component Diagram Pattern

```
┌─────────────────────────────────────────────────────────┐
│                      System Name                         │
├─────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐      ┌──────────────┐                 │
│  │  Component A │ ───→ │  Component B │                 │
│  └──────────────┘      └──────────────┘                 │
│         │                     │                          │
│         ↓                     ↓                          │
│  ┌──────────────┐      ┌──────────────┐                 │
│  │  Component C │ ←─── │  Component D │                 │
│  └──────────────┘      └──────────────┘                 │
│                                                          │
└─────────────────────────────────────────────────────────┘
```

---

## Flow Diagram Pattern

```
┌─────────┐     ┌─────────┐     ┌─────────┐
│  Start  │ ──→ │ Process │ ──→ │   End   │
└─────────┘     └─────────┘     └─────────┘
                    │
                    ↓
               ┌─────────┐
               │ Decision│
               └─────────┘
                 │     │
            Yes ↓     ↓ No
           ┌─────┐ ┌─────┐
           │  A  │ │  B  │
           └─────┘ └─────┘
```

---

## Layer Diagram Pattern

```
┌─────────────────────────────────────────┐
│            Presentation Layer            │
├─────────────────────────────────────────┤
│             Business Layer               │
├─────────────────────────────────────────┤
│              Data Layer                  │
└─────────────────────────────────────────┘
```

---

## Best Practices

### 1. Consistency
- Use consistent box sizes for similar components
- Align elements horizontally and vertically
- Use consistent spacing

### 2. Clarity
- Keep diagrams simple and focused
- Use clear labels
- Avoid crossing lines when possible

### 3. Readability
- Use adequate whitespace
- Group related components
- Add legends for complex diagrams

### 4. Compatibility
- Use standard ASCII characters when possible
- Test rendering in different environments
- Provide text alternatives for complex diagrams

---

## Validation

Before including ASCII diagrams:
1. Verify all box characters connect properly
2. Check alignment in monospace font
3. Ensure diagram renders correctly in markdown
4. Test in target documentation environment
