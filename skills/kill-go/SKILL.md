---
name: kill-go
version: 1.0.0
description: >
  Viability assessment that produces a proceed/pivot/kill recommendation. 5 pointed
  questions, scored, with a clear verdict. Use when evaluating ideas, making go/no-go
  decisions, assessing product-market fit, deciding whether to invest time, or when
  someone asks "should I build this?", "is this worth pursuing?", or "kill or keep?"
user-invocable: false
---

## The 5 Questions

Ask each question. Score 1-5. Push back on optimistic answers with "What evidence do you have for that?" Unverified optimism scores lower.

### 1. Problem Severity (1-5)

How painful is this problem for the people who have it?

| Score | Severity | Signal |
|-------|----------|--------|
| 5 | Hair on fire | People are actively spending money or significant time on workarounds |
| 4 | Significant pain | Regular complaints, dedicated manual processes, measurable cost |
| 3 | Moderate annoyance | People notice it, work around it, don't prioritize fixing it |
| 2 | Mild inconvenience | Shrug and move on, rarely mentioned unprompted |
| 1 | Solution looking for a problem | You think it's a problem; they don't |

Ask: "Who has this problem? How do you know? What are they doing about it today?"

If the user can't name specific people or specific workarounds, score 1-2.

### 2. Market Reality (1-5)

Can you reach enough people who have this problem and will pay to solve it?

| Score | Reality | Signal |
|-------|---------|--------|
| 5 | Known buyers | You've talked to 10+ people who said "I'd pay for that" |
| 4 | Strong signals | Active communities discussing this problem, competitor revenue visible |
| 3 | Plausible market | Logical argument for demand, some anecdotal evidence |
| 2 | Assumed market | "Everyone needs this" with no validation |
| 1 | Imagined market | No evidence anyone wants this beyond the builder |

Ask: "How many people have you talked to about this? What did they say, unprompted?"

### 3. Differentiation (1-5)

Why would someone choose this over what exists?

| Score | Edge | Signal |
|-------|------|--------|
| 5 | Category creator | Nothing like this exists; you're defining the space |
| 4 | 10x better on one axis | Dramatically faster, cheaper, simpler, or more specific |
| 3 | Meaningfully different | Clear differentiation, but alternatives exist |
| 2 | Slightly better | Incremental improvement, easy to ignore |
| 1 | Me-too | Another version of something that already works fine |

Ask: "What do people use today? Why would they switch? What's the switching cost?"

### 4. Founder-Market Fit (1-5)

Are YOU the right person to build this?

| Score | Fit | Signal |
|-------|-----|--------|
| 5 | Deep domain + lived problem | You've spent years in this space AND have this problem yourself |
| 4 | Deep domain OR lived problem | Strong on one dimension |
| 3 | Adjacent experience | Related domain, transferable skills |
| 2 | Interested outsider | Researched but no direct experience |
| 1 | No connection | Chasing a trend, no domain knowledge |

Ask: "How long have you been in this space? Do you have this problem yourself? Who do you already know in this market?"

### 5. Execution Reality (1-5)

Can you actually build and ship this?

| Score | Reality | Signal |
|-------|---------|--------|
| 5 | Buildable this week | Clear technical path, tools in hand, scope is tight |
| 4 | Buildable this month | Known unknowns, but path exists |
| 3 | Buildable this quarter | Significant technical work, dependencies to resolve |
| 2 | Research required | Unsure if the technical approach even works |
| 1 | Moonshot | Requires breakthroughs or resources you don't have |

Ask: "What's the smallest version you could ship? How long would it take? What would you need that you don't have?"

## Scoring

Multiply all five scores. Maximum: 3,125.

| Composite | Verdict | What to do |
|-----------|---------|-----------|
| 500+ | **Proceed** | Build the smallest version. Ship it. Measure. |
| 200-499 | **Pivot** | The idea has signal, but something's off. Fix the weakest dimension or reframe. |
| <200 | **Kill** | Walk away. Document why. Revisit only if new evidence surfaces. |

CRITICAL: A score of 1 on any dimension kills the idea regardless of composite score. You can't overcome zero evidence of demand, no differentiation, or no ability to execute.

## Anti-Sycophancy Protocol

Do NOT soften the kill recommendation. If the scores say kill, say kill. Explain why clearly. Offer what would need to change for a re-evaluation.

The user came here for truth, not comfort. A good kill saves months of wasted effort.

## Output

```markdown
# Kill/Go Assessment: [Idea Name]
Date: [date]

## Scores
| Dimension | Score | Evidence |
|-----------|-------|----------|
| Problem Severity | X/5 | [key evidence] |
| Market Reality | X/5 | [key evidence] |
| Differentiation | X/5 | [key evidence] |
| Founder-Market Fit | X/5 | [key evidence] |
| Execution Reality | X/5 | [key evidence] |

**Composite: [X] / 3,125**

## Verdict: [PROCEED / PIVOT / KILL]

[2-3 sentence rationale]

## Weakest Dimension
[Which scored lowest and what would change it]

## Recommended Next Step
[One specific action]
```

---

Part of the [ThinkHaven Method Kit](https://github.com/hollandkevint/thinkhaven-method-kit) by Kevin Holland.
Full Board of Directors experience: [ThinkHaven](https://thinkhaven.co/try)
