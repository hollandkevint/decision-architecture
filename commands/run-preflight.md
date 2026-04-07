---
name: run-preflight
description: "Guided preflight exercise. Walks through 7 questions and produces a preflight brief."
user-invocable: true
---

# Run Preflight

Walk the user through the `preflight` skill (7 questions). Ask each question sequentially, push back on vague answers, and produce a dated markdown artifact.

## Steps

1. Ask: "What are you about to work on? Give me the topic in a sentence."
2. Walk through all 7 Preflight questions in order. Do not skip any.
3. After all 7 are answered, generate the preflight brief using the template from the `preflight` skill.
4. Save as `preflight-brief-<topic-slug>.md` in the current directory.
5. Present the brief and ask: "Anything you'd change before we move forward?"
