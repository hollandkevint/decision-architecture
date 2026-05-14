# ThinkHaven Method Kit

Open decision architecture for people who need sharper judgment before they build, pitch, publish, or advise.

This is the public method layer behind [ThinkHaven](https://thinkhaven.co): prompts, skills, playbooks, and frameworks for turning messy ideas into defensible decisions. Run the methods manually from this repo, or use ThinkHaven when you want the hosted version with adaptive facilitation, memory, artifacts, and a personal board of advisors.

## Start here

If you are a PMM, product manager, founder, writer, or consultant with an idea that needs pressure, start with:

- **[`b2b-idea-vetting`](skills/b2b-idea-vetting/SKILL.md)** — a 20-minute session for vetting a B2B idea, positioning angle, offer, content thesis, or client recommendation.

It produces a short decision artifact:

- decision under review
- strongest case
- weakest assumption
- evidence gaps
- recommended next move
- confidence level

## Install

```bash
/plugin marketplace add hollandkevint/thinkhaven-method-kit
```

Or copy individual files from `skills/`, `prompts/`, and `frameworks/` into your own AI workspace.

## What this is

ThinkHaven Method Kit is for the moment before commitment:

- before you build the feature
- before you sell the offer
- before you publish the point of view
- before you recommend the strategy to a client
- before you walk into the meeting where the decision has to hold up

The kit is intentionally lightweight. It does not try to be a self-hosted ThinkHaven clone. It exposes the method: the questions, pressure tests, briefs, and anti-sycophancy patterns that make decisions harder to fool yourself about.

## What's inside

### Skills

| Skill | What it does |
|-------|-------------|
| **b2b-idea-vetting** | 20-minute pressure test for a B2B idea, positioning angle, offer, content thesis, or client recommendation. Produces a concrete decision artifact. |
| **preflight** | 7-question exercise before any AI session. Forces clarity on outcomes, failure modes, and hard parts. Based on Nate Jones' Preflight. |
| **grill-me** | Decision tree exploration. Uses classic grill-me when there is no reference context, and docs-aware grill-with-docs behavior when a codebase, project, glossary, docs, or prior decisions are available. |
| **kill-go** | 5 pointed questions that produce a viability score and a proceed/pivot/kill recommendation. |
| **assumption-mapper** | Extract and rank assumptions from any idea. Identifies what to test first. |
| **pull-framework** | Project/Urgent/List/Limitations. Structured problem discovery before solution design. |
| **decision-brief** | One-page decision brief that passes the Simple/Surprising/Easy test. |
| **arbitrage-audit** | 3 diagnostic questions: What inefficiency is this built on? How fast can AI close it? What new gap does closure create? |
| **ai-graduation** | 7-move decision gate for AI deployment: contain, instrument, verify, prove, narrow, widen, standardise. |
| **problem-framing** | 9-step systematic diagnosis. Define, diagnose, root cause, force analysis, solution generation, evaluation. |
| **innovation-diagnostic** | Lightweight innovation assessment. Strategic context, market analysis, disruption identification, go/no-go gates. |
| **design-thinking-lite** | 7-step human-centered design: context, empathize, define, ideate, prototype, test, iterate. |

### Agents

| Agent | What it does |
|-------|-------------|
| **decision-facilitator** | Threads one decision across stages: framing intake, pressure tests, assumption mapping, and decision brief. Anti-sycophancy first. Invoke via `/da:decide` or `@decision-facilitator`. |

### Commands

| Command | Output |
|---------|--------|
| `/da:decide` | Runs the decision-facilitator agent end-to-end. Decision-brief output. |
| `/da:run-preflight` | `preflight-brief-<name>.md` |
| `/da:challenge-idea` | `challenge-report-<name>.md` |
| `/da:map-arbitrage-gaps` | `gap-map-<name>.md` |
| `/da:diagnose-problem` | `problem-diagnosis-<name>.md` |
| `/da:validate-innovation` | `innovation-assessment-<name>.md` |

### Prompts

Works with any LLM:

- **anti-sycophancy-system-prompt** — forces pushback instead of validation
- **board-of-directors** — multi-perspective prompt with advisors who disagree
- **grill-me-non-coding** — decision tree exploration for strategy, hiring, GTM, or any non-code decision; optionally docs-aware when project context is provided
- **arbitrage-gap-diagnostic** — 3 questions for evaluating any market or industry

### Frameworks

Reference documents for decision architecture practice:

- **four-layer-decision-engineering** — Dashboard Craft > Decision Context > Decision Intent > Decision Infrastructure
- **cognitive-extensions-taxonomy** — Maps cognitive modes to decision session types

## ThinkHaven vs. the Method Kit

| Use this repo when... | Use ThinkHaven when... |
|-----------------------|------------------------|
| You want a transparent method you can inspect, fork, and run manually. | You want a guided session that adapts to your answers. |
| You are testing whether a prompt or playbook helps your thinking. | You want memory, artifacts, and board-style pressure over time. |
| You want to bring the method into your own AI workspace. | You need a decision you can defend and share. |
| You have a plan and no reference material: use `grill-me`. | You want a paste-driven hosted plan grill: use `https://thinkhaven.co/try?mode=plan-grill`. |
| You have a codebase, project docs, glossary, or prior decisions: use `grill-me` in docs-aware mode. | You want docs-aware facilitation plus saved session artifacts. |

ThinkHaven is the hosted execution layer. This repo is the open method.

## The thesis

When building cost approaches zero, the scarce resource is knowing what to build. These skills structure the path from "I have an idea" to "I know what to do." See [PHILOSOPHY.md](PHILOSOPHY.md) for the full argument.

## Examples

- [`jonathan-style-content-angle.md`](examples/jonathan-style-content-angle.md) — vetting a B2B content/positioning angle
- [`product-manager-feature-bet.md`](examples/product-manager-feature-bet.md) — vetting a product feature bet

## Related

- **[ThinkHaven](https://thinkhaven.co/try)** — The hosted Board of Directors experience: AI advisors with distinct worldviews who pressure-test your strategy
- **[BMAD-METHOD](https://github.com/bmad-code-org/BMAD-METHOD)** — Full agent framework with 21+ specialized agents and 50+ workflows
- **[data-product-operator](https://github.com/hollandkevint/data-product-operator)** — Skills for data product managers

## Credits

- Nate Jones — Preflight framework, Arbitrage Gap taxonomy
- Matt Pocock — MIT-licensed grill-me, grill-with-docs, and ubiquitous-language skill patterns
- Frederick P. Brooks — "The Design of Design" decision tree concept
- Stuart Winter-Tear — AI Graduation Path
- Alex MH Smith — Creative brief test: Simple, Surprising, Easy
- Pavel Samsonov — Problem framing philosophy
- BMAD Creative Intelligence Suite — Problem-solving, innovation strategy, design thinking workflows

## License

MIT
