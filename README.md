# Decision Architecture

Structured thinking before you build. A Claude Code plugin with 11 skills, 5 commands, and 4 prompts for making better decisions.

## Install

```bash
/plugin marketplace add hollandkevint/decision-architecture
```

Or add individual skills manually by copying the `skills/` directory into your project.

## What's inside

### Skills

| Skill | What it does |
|-------|-------------|
| **preflight** | 7-question exercise before any AI session. Forces clarity on outcomes, failure modes, and hard parts. Based on Nate Jones' Preflight. |
| **grill-me** | Decision tree exploration. "Interview me relentlessly about every aspect of this plan." Non-coding variant of Matt Pocock's viral skill. |
| **kill-go** | 5 pointed questions that produce a viability score and a proceed/pivot/kill recommendation. |
| **assumption-mapper** | Extract and rank assumptions from any idea. Identifies what to test first. |
| **pull-framework** | Project/Urgent/List/Limitations. Structured problem discovery before solution design. |
| **decision-brief** | One-page decision brief that passes the Simple/Surprising/Easy test. |
| **arbitrage-audit** | 3 diagnostic questions: What inefficiency is this built on? How fast can AI close it? What new gap does closure create? |
| **ai-graduation** | 7-move decision gate for AI deployment: contain, instrument, verify, prove, narrow, widen, standardise. |
| **problem-framing** | 9-step systematic diagnosis. Define, diagnose, root cause, force analysis, solution generation, evaluation. |
| **innovation-diagnostic** | Lightweight innovation assessment. Strategic context, market analysis, disruption identification, go/no-go gates. |
| **design-thinking-lite** | 7-step human-centered design: context, empathize, define, ideate, prototype, test, iterate. |

### Commands

| Command | Output |
|---------|--------|
| `/da:run-preflight` | `preflight-brief-<name>.md` |
| `/da:challenge-idea` | `challenge-report-<name>.md` |
| `/da:map-arbitrage-gaps` | `gap-map-<name>.md` |
| `/da:diagnose-problem` | `problem-diagnosis-<name>.md` |
| `/da:validate-innovation` | `innovation-assessment-<name>.md` |

### Prompts

Works with any LLM (Claude, ChatGPT, etc.):

- **anti-sycophancy-system-prompt** — System prompt that forces pushback instead of validation
- **board-of-directors** — Multi-perspective prompt with advisors who disagree
- **grill-me-non-coding** — Decision tree exploration for strategy, hiring, GTM, any non-code decision
- **arbitrage-gap-diagnostic** — 3 questions for evaluating any market or industry

### Frameworks

Reference documents for decision architecture practice:

- **four-layer-decision-engineering** — Dashboard Craft > Decision Context > Decision Intent > Decision Infrastructure
- **cognitive-extensions-taxonomy** — Maps cognitive modes to decision session types

## The thesis

When building cost approaches zero, the scarce resource is knowing what to build. These skills structure the path from "I have an idea" to "I know what to do." See [PHILOSOPHY.md](PHILOSOPHY.md) for the full argument.

## Related

These skills are lightweight, standalone decision tools. For deeper systems:

- **[BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)** — Full agent framework with 21+ specialized agents and 50+ workflows
- **[data-product-operator](https://github.com/hollandkevint/data-product-operator)** — 14 skills for data product managers (discovery, validation, metrics, modeling)
- **[ThinkHaven](https://thinkhaven.co/try)** — The full Board of Directors experience: 6 AI advisors with distinct worldviews who pressure-test your strategy

## Credits

- Nate Jones — Preflight framework, Arbitrage Gap taxonomy
- Matt Pocock — grill-me skill pattern (adapted with attribution)
- Frederick P. Brooks — "The Design of Design" (decision tree concept)
- Stuart Winter-Tear — AI Graduation Path
- Alex MH Smith — Creative brief test (Simple/Surprising/Easy)
- Pavel Samsonov — Problem framing philosophy
- BMAD Creative Intelligence Suite — Problem-solving, innovation strategy, design thinking workflows

## License

MIT
