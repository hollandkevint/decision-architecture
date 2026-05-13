# The Four Layers of Decision Engineering

A framework for moving from "we ship dashboards" to "we enable decisions."

## The Parallel

| What "prompting" became | What "analytics" is becoming |
|---|---|
| Prompt Craft (structured queries) | Dashboard Craft (structured reports) |
| Context Engineering (information environment) | Decision Context (what the org needs to know before looking at data) |
| Intent Engineering (encoded values/tradeoffs) | Decision Intent (what the org optimizes for when metrics conflict) |
| Specification Engineering (autonomous execution) | Decision Infrastructure (self-serve decision systems that work without the analyst in the room) |

## Layer 1: Dashboard Craft

Where most teams are. They build good dashboards. Reports are clean. SQL is tested. This is table stakes — necessary, not sufficient.

**Diagnostic:** Ask your team: "Name 3 decisions that changed because of something we shipped last quarter." If they can't, you have a Layer 1 ceiling.

## Layer 2: Decision Context

What does the stakeholder need to know BEFORE opening the dashboard? What's the business context, the metric definitions, the known limitations?

A dashboard without context is a chart without a caption. The analyst who ships a dashboard and a one-page "how to use this" document is already at Layer 2.

**Diagnostic:** For every dashboard, can a new person understand what it means without asking you?

## Layer 3: Decision Intent

When the revenue metric and the retention metric conflict, which wins? When speed and accuracy trade off, what's the default?

Most data teams have never encoded this. They say "that's a business decision, not a data decision." That IS the point. If you're not encoding business intent into your data systems, you're shipping numbers and hoping someone else figures out what they mean.

**Diagnostic:** When two metrics conflict, does the team know which one wins — without escalating?

## Layer 4: Decision Infrastructure

Self-serve systems where the decision-maker can get from question to answer without pinging the data team. Not just a dashboard, but a dashboard + context doc + intent framework + evaluation criteria.

This is the end state. Most teams are years away from it. Knowing the destination changes how you build today.

**Diagnostic:** Can a stakeholder make a data-informed decision at 6am on their phone without emailing your team?

## The Key Line

"Analytics engineering answered 'how do we build trustworthy data?' It never answered 'how do we make sure someone actually uses it to decide something.'"

---

From the Decision Engineering blog series by Kevin Holland.
Full toolkit: [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit)
