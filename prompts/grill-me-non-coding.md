# Grill-Me: Non-Coding Variant

Decision tree exploration for strategy, hiring, GTM, product decisions, course
design, client recommendations, or any non-code decision. Adapted from Matt
Pocock's grill-me pattern and extended with an optional docs-aware mode.

## The Prompt

```text
Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the decision tree, resolving dependencies between decisions one by one.

For each question, provide your recommended answer. Ask one question at a time and wait for my answer before continuing.

If I only give you a plan, use classic grill-me: pressure-test the decision tree, assumptions, risks, and next action.

If I give you project docs, domain terms, prior decisions, a glossary, or other reference context, use grill-with-docs behavior: challenge the plan against that context, sharpen overloaded terms, flag contradictions, and capture any glossary or ADR-worthy decisions. Do not claim access to files or code unless I have pasted them or your environment actually exposes them.
```

## When to Use

- Planning a go-to-market strategy
- Making a hiring decision
- Designing a course or workshop
- Evaluating a business model
- Pressure-testing a product or feature plan
- Checking a plan against project docs, domain language, or prior decisions
- Any decision with multiple interdependent sub-decisions

## What to Expect

A 20-45 minute session with 15-50 questions. The AI walks every branch of your
decision tree, surfacing dependencies and forcing clarity on things you have not
fully thought through.

When there is no reference context, this stays as pure decision tree
exploration. When you provide docs or project context, the AI also checks the
plan against the language and decisions already present in that context.

## Optional Docs-Aware Outputs

Use these only when the user provides or points to project/domain context:

- **Domain context:** Canonical terms, aliases to avoid, relationships, example
  dialogue, and flagged ambiguities.
- **Decision record:** Resolved decisions, open questions, assumptions, risks,
  and ADR-worthy choices.

An ADR-worthy choice must be hard to reverse, surprising without context, and
the result of a real trade-off.

## Credit

Original grill-me, grill-with-docs, and ubiquitous-language skill patterns by
Matt Pocock. Adapted for the ThinkHaven Method Kit by Kevin Holland under MIT
license-compatible attribution.

For the full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
