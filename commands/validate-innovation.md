---
name: validate-innovation
description: "Innovation assessment with go/no-go gates. Evaluates market opportunity, competitive reality, and disruption potential."
user-invocable: true
---

# Validate Innovation

Run the `innovation-diagnostic` skill through all 5 gates.

## Steps

1. Ask: "What's the opportunity you want to assess? Give me the elevator pitch."
2. Walk through all 5 gates of the `innovation-diagnostic` skill.
3. A "no" at any gate pauses the assessment with a clear explanation.
4. If all gates pass, produce the go/investigate/no-go verdict.
5. Save as `innovation-assessment-<opportunity-slug>.md` in the current directory.
