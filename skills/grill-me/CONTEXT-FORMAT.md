# Domain Context Format

Use this format when grill-me is running in docs-aware mode and the session has
resolved project or domain language worth preserving.

```md
# {Context Name}

{One or two sentences describing what this context is and why it exists.}

## Language

**{Canonical Term}**: {One-sentence definition of what the term is.}
_Avoid_: {Alias}, {ambiguous synonym}

**{Another Term}**: {One-sentence definition of what the term is.}
_Avoid_: {Alias}

## Relationships

- A **{Term}** belongs to exactly one **{Other Term}**
- A **{Term}** can produce one or more **{Other Terms}**

## Example Dialogue

> **Dev:** "When a **{Term}** changes state, does it affect the **{Other Term}**?"
> **Domain expert:** "Only when {specific boundary condition}."

## Flagged Ambiguities

- "{ambiguous word}" was used to mean both **{Term A}** and **{Term B}**. Resolve by using **{Term A}** for {definition} and **{Term B}** for {definition}.
```

## Rules

- Be opinionated. Pick one canonical term and list aliases to avoid.
- Flag conflicts explicitly. Ambiguity is an output, not a failure.
- Keep definitions tight. One sentence max. Define what it is, not what it does.
- Keep it implementation-free. Do not include modules, classes, endpoints, or
  implementation choices unless they are also the domain language.
- Show relationships. Use bold term names and cardinality where obvious.
- Include only terms specific to this domain or project context.
- Group terms under subheadings when natural clusters emerge.
- Write a short example dialogue that shows the terms interacting naturally.

## Single vs. Multi-Context Projects

Most projects can use one context document. If the project clearly has multiple
bounded contexts, keep separate context documents and add a short map that
describes where each context lives and how the contexts relate.
