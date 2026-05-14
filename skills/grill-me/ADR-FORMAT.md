# ADR Format

Use this format when grill-me is running in docs-aware mode and a decision is
worth preserving for future readers.

## When to Record an ADR

Only record an ADR when all three are true:

1. **Hard to reverse:** The cost of changing the decision later is meaningful.
2. **Surprising without context:** A future reader would wonder why this choice
   was made.
3. **Real trade-off:** There were genuine alternatives and one was chosen for
   specific reasons.

If a decision is easy to reverse, obvious, or not the result of a real
alternative, skip the ADR.

## Template

```md
# {Short title of the decision}

{One to three sentences: what context forced the decision, what was decided, and
why this option was chosen over plausible alternatives.}
```

That can be the entire ADR. The point is to preserve that the decision was made
and why, not to fill out a long template.

## Optional Sections

Only add these when they create real value:

- **Status:** `proposed`, `accepted`, `deprecated`, or `superseded by ADR-NNNN`
- **Considered Options:** Rejected alternatives that are likely to be raised
  again
- **Consequences:** Non-obvious downstream effects

## Good ADR Candidates

- Architectural shape
- Integration patterns between contexts
- Technology choices with meaningful lock-in
- Boundary and ownership decisions
- Deliberate deviations from the obvious path
- Constraints not visible in the code or docs
- Non-obvious rejected alternatives
