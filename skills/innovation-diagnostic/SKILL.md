---
name: innovation-diagnostic
version: 1.0.0
description: >
  Lightweight innovation assessment with go/no-go gates. Strategic context, market
  analysis, disruption identification, and recommendation. Adapted from BMAD Creative
  Intelligence Suite (Victor). Activates on "assess this opportunity", "innovation",
  "disruption", "market opportunity", "blue ocean", "jobs to be done", "is there a
  market for this", or "competitive landscape."
user-invocable: false
---

## The Assessment (5 Gates)

Walk through each gate. A "no" at any gate stops the assessment with a clear explanation. Brutal truth over comfortable assumptions.

### Gate 1: Strategic Context

Ask: "What's the current situation? What triggered this idea? What constraint or opportunity are you responding to?"

Establish:
- Where the user sits (startup founder, product leader, executive, consultant)
- What resources are available (time, money, team, domain expertise)
- What's the time horizon (this quarter, this year, 3+ years)
- What's already been tried

If the user can't articulate why NOW, probe deeper. Timing matters more than the idea.

### Gate 2: Problem-Market Fit

Ask: "Who has the problem you're solving? How do you know they have it? What are they doing about it today?"

Evaluate using Jobs-to-be-Done:
- **Functional job:** What task are they trying to accomplish?
- **Emotional job:** How do they want to feel?
- **Social job:** How do they want to be perceived?

CRITICAL: If the user can't name specific people with specific workarounds, the market is imagined. Flag this directly. "You've described a market you think exists. What evidence do you have?"

### Gate 3: Competitive Reality

Ask: "What exists today that addresses this? Why hasn't someone solved this already?"

Map the landscape:
- **Direct competitors:** Same solution, same problem
- **Indirect competitors:** Different solution, same problem (includes "do nothing")
- **Substitutes:** Same outcome, different approach entirely

The question "Why hasn't someone solved this?" has only a few honest answers:
1. They have, and you haven't found it yet (most common)
2. The market is too small to attract investment
3. The technology or conditions didn't exist until now
4. The incumbent is complacent or structurally unable to adapt

If the answer is #1, the assessment should pivot to differentiation, not originality.

### Gate 4: Disruption Potential

Where does this idea sit on the innovation spectrum?

| Type | Description | Risk/Reward |
|------|-------------|-------------|
| **Sustaining** | Better version of what exists | Low risk, low ceiling |
| **Low-end disruption** | "Good enough" at dramatically lower cost/complexity | Medium risk, high potential |
| **New-market disruption** | Serves non-consumers (people who couldn't access the current solution) | High risk, category-defining |

Ask: "Are you making the existing thing better, making it dramatically cheaper/simpler, or reaching people who can't access the current solution?"

The honest answer determines the strategy. Sustaining innovation competes on features. Disruption competes on access or simplicity.

### Gate 5: Go/No-Go

Synthesize Gates 1-4 into a recommendation:

| Signal | Verdict |
|--------|---------|
| Clear problem + known market + differentiated position + timing makes sense | **Go** — define the smallest version and ship |
| Strong signals but one weak gate | **Investigate** — name the weak gate, design a cheap test |
| Multiple weak gates or imagined market | **No-go** — document why, revisit when evidence changes |

## Output

```markdown
# Innovation Assessment: [Opportunity Name]
Date: [date]

## Strategic Context
[Gate 1 summary]

## Problem-Market Fit
- Functional job: [what they're trying to do]
- Evidence of demand: [specific signals or "none found"]

## Competitive Reality
[Gate 3 map]

## Disruption Type
[Sustaining / Low-end / New-market] — [rationale]

## Verdict: [GO / INVESTIGATE / NO-GO]
[2-3 sentence rationale]

## If Go: Smallest Shippable Version
[What to build first]

## If Investigate: Cheapest Test
[How to validate the weak gate]
```

Adapted from BMAD Creative Intelligence Suite innovation-strategy workflow (Victor).

---

Part of the [Decision Architecture](https://github.com/hollandkevint/decision-architecture) toolkit by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
