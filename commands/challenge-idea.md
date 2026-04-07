---
name: challenge-idea
description: "Full challenge session combining kill-go scoring, assumption mapping, and grill-me. Produces a challenge report."
user-invocable: true
---

# Challenge Idea

Run a comprehensive challenge session that combines three skills: `kill-go` (viability scoring), `assumption-mapper` (hidden assumptions), and `grill-me` (decision tree exploration).

## Steps

1. Ask: "What's the idea, plan, or strategy you want challenged? Pitch it to me in 2-3 minutes."
2. Run the `kill-go` assessment (5 questions, scored 1-5, composite score, proceed/pivot/kill verdict).
3. Run the `assumption-mapper` (extract assumptions, rank by impact/confidence, identify "test immediately" items).
4. For any dimension that scored 3 or below in kill-go, use `grill-me` to explore that branch of the decision tree exhaustively.
5. Synthesize into a challenge report.
6. Save as `challenge-report-<idea-slug>.md` in the current directory.

## Output includes:
- Kill/Go scorecard with evidence
- Assumption map with test priorities
- Deep exploration of weak areas
- Final verdict with recommended next action
