# agent-bootstrap

Minimal bootstrap rules for high-quality agentic projects.

If you're a human point your coding agent at this file to bootstrap a new project.
If you are an agent using this, load the major sections into context, then follow `## onboarding-process`.

## recommendations

- scripts are mainly dumb pipes.
- skills are reusable units of know-how: they define how to perform one class of work, including the instructions, tools, and checks that make that work reliable.
- recipes are skill-specific specializations that adapt how a skill is instructed for a particular kind of task or output.
- pipelines define the default stages or steps for a task family, and can be adapted for a specific run by adding, skipping, reordering, retrying steps, or escalating to the user when required. Pipelines should produce auditable decisions and artifacts.
- config holds explicit parameters and contracts.
- code stays minimal unless it is itself the artifact being improved.
- sub-agents are useful for bounded, parallelizable parts of a pipeline, especially read-heavy or evaluative work; avoid using them by default for concurrent write-heavy tasks.
- make the runtime observable: agents and humans should be able to inspect logs, traces, metrics, state, and artifacts to understand what happened.
- define explicit evals: important outcomes should be judged by clear, repeatable, and quantitative criteria. Evals provide the optimization signal.
- docs should be structured, versioned, and mechanically maintained so agents can trust and navigate them.
- optimize for predictable discovery.
- focus documentation on the non-obvious.
- tests, linters, and eval harnesses should encode important invariants so agents can validate, debug, and improve the system autonomously.
- start with the minimum useful structure; only add complexity when it improves reliability, reuse, or measurability.
- ask for clarification when instructions are unclear, and adapt explanations and vocabulary to the user's level of technical understanding.
- continuously optimize your harness to best follow these recommendations.

Most improvement happens in skills, recipes, and pipelines, and sometimes in code when code itself is the artifact being improved.

## minimal opinionated setup

- put an AGENTS.md at the root describing the project, its structure, and where agents should look first.
- keep a **`docs/`** folder for project context, plans, decisions, eval definitions, and quality criteria.
- keep a **`skills/`** folder for reusable units of know-how. Specify skills using the open standard and spec defined at [https://agentskills.io/specification](https://agentskills.io/specification).
- recipes are in the skill folder with specific guidelines and learning on using the skill based on use-cases. Write in skill/references/recipes/YOUR_RECIPE.md.
- scan `## references` for concrete examples when stuck.

## references

- writing effective AGENTS.md files: [lessons from 2,500+ repositories](https://github.blog/ai-and-ml/github-copilot/how-to-write-a-great-agents-md-lessons-from-over-2500-repositories/)
- writing skills: [the complete guide to building skills for Claude](https://resources.anthropic.com/hubfs/The-Complete-Guide-to-Building-Skill-for-Claude.pdf) and the [agent skills specification](https://agentskills.io/specification)
- harness engineering: [OpenAI on leveraging Codex in an agent-first world](https://openai.com/index/harness-engineering/)

## onboarding-process

If unclear, ask these questions to the user up front, all at once:

- what is the project, in one sentence?
- what are the intended inputs, outputs, constraints, and relevant domain context?
- what is the user's level of technical understanding?
- should the opinionated setup be used? Defaults to yes.

Then:

1. create an `AGENTS.md` file, encode our `## recommendations` adapting where the project requires it. If the user is not technical, take responsibility for technical decisions and communicate accordingly.
2. set up the project following the opinionated setup unless the user explicitly rejects it.
3. begin work using the goals, context, and constraints gathered during onboarding.
