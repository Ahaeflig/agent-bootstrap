# agent-bootstrap

A minimal bootstrap for high-quality agentic projects.

If you are an agent using this to start or update a project, load the major sections into context, then follow `## onboarding-process`.

## core recommendations

- scripts are mainly dumb pipes.
- skills are reusable units of know-how: they define how to perform one class of work, including the instructions, tools, and checks that make that work reliable.
- recipes are skill-specific specializations that adapt how a skill is instructed for a particular kind of task or output.
- pipelines define the default stages or steps for a task family, and can be adapted for a specific run by adding, skipping, reordering, or retrying steps when required. Should produce auditable decisions and artifacts.
- config holds explicit parameters and contracts.
- code stays minimal unless it is itself the artifact being improved.
- sub-agents are useful for bounded, parallelizable parts of a pipeline, especially read-heavy or evaluative work; avoid using them by default for concurrent write-heavy tasks.
- make the runtime observable: agents and humans should be able to inspect logs, traces, metrics, state, and artifacts to understand what happened.
- define explicit evals: important outcomes should be judged by clear, repeatable, and quantitative criteria. Evals provide the optimization signal.
- docs should be structured, versioned, and mechanically maintained so agents can trust and navigate them.
- optimize for predictable discovery.
- avoid documenting the obvious, agents are likely to know or infer reliably many things.
- tests, linters, and eval harnesses should encode important invariants so agents can validate, debug, and improve the system autonomously.
- start with the minimum useful structure; only add complexity when it improves reliability, reuse, or measurability.
- ask for clarification when instructions are unclear, and adapt explanations and vocabulary to the user's level of technical understanding.
- continuously optimize your harness to best follow these recommendations.

Most improvement happens in skills, recipes, and pipelines, and sometimes in code when code itself is the artifact being improved.

## opinionated setup

- put an **`AGENTS.md`** file at the project root, it is the project's operating map, a glance and any agent should have the context to figure out where to find what they need.
- keep a **`docs/`** folder for project context, plans, decisions, eval definitions, and quality criteria.
- keep a **`skills/`** folder for reusable units of know-how. Specify skills using the open standard and spec defined at [https://agentskills.io/specification](https://agentskills.io/specification).
- recipes are in the skill folder with specific guidelines and learning on using the skill based on use-cases. Write in skill/references/recipes/YOUR_RECIPE.md.

## onboarding-process

Ask these questions up front, all at once:

- what is the project, in one sentence?
- what are the intended inputs, outputs, constraints, and relevant domain context?
- what is the user's level of technical understanding?
- should the opinionated setup be used? Defaults to yes.

Then:

1. create an `AGENTS.md` file using the core recommendations, adapting only where the project clearly requires it. If the user is not technical, take responsibility for technical decisions and communicate accordingly.
2. set up the project following the opinionated setup unless the user explicitly rejects it.
3. begin work using the goals, context, and constraints gathered during onboarding.
