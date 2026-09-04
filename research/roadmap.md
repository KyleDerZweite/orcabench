# Roadmap

This is a documentation-first WIP. Each step should produce inspectable evidence before the next step expands the workload.

## 1. Prove one execution path

Pin OpenCode, inspect its current CLI and session API, and run a tiny solo/team integration test using the proposed route. Establish model selection, tool execution, supported effort settings, descendant accounting, cancellation, and external verification. Record failures and unknown fields. Done means another maintainer can reproduce the test from the recorded task and configuration.

Harbor is optional at this step. Adopt it when its container and task support removes more work than the integration adds. Keep the native agent behavior intact.

## 2. Prepare two tasks and a judging view

Write the first two public-safe task packages, each with a frozen start state, prompt, requirements, and an independent verifier. Prepare a small private artifact comparison view or use an existing local review workflow. Collect practice ballots from both maintainers, fix confusing presentation, and freeze the guidance. Done means both can inspect and judge artifacts without seeing contestant identity or each other's vote.

## 3. Freeze and run the screen

Finish six task packages. Freeze eight configurations, their actual cost/deadline/concurrency limits, the task mix, rerun policy, pair-selection rule, and scoring definitions in a numbered protocol. Produce 48 runs if all routes are supported. Publish any reduced matrix explicitly rather than silently substituting models. Done means every planned run has an artifact or documented terminal failure, accounting completeness, and verifier result.

## 4. Judge and publish evidence

Collect independent ballots, preserve disagreement, and publish the eligible prompts, artifacts, checks, highlighted concerns, per-rater outcomes, and resource data. Begin with direct comparisons and descriptive percentages. Mark the batch as exploratory. Done means a reader can trace every displayed number to the relevant runs and ballots.

## 5. Confirm useful finalists

Choose finalists, freeze them, and prepare fresh tasks. Set the confirmation workload using the effect size that matters and variability observed in the screen. Add repeats where reliability matters. Done means the report distinguishes discovery from confirmation and states the task mix over which its conclusion applies.

## 6. Expand when there is a concrete question

Possible issue topics:

- Same-model workers versus cheap workers, including controller integration cost.
- A mixed Luna/GLM pool versus the best fixed worker choice.
- High versus max effort on fresh tasks, including deceptively simple tasks.
- Production skill present versus absent, with an immutable skill version.
- A second native harness, separating practical product comparison from a matched harness experiment.
- Reproducible worker timeout, wrong fact, stale context, contradiction, or injected instruction.
- Blender scene tasks with editable artifacts, geometric checks, and standardized renders.
- Oracle decomposition and naive fan-out to diagnose delegation decisions.
- Nested delegation with explicit depth and concurrency limits.
- Evidence dossiers, data audits, and constraint scheduling tasks.
- A batch Bradley-Terry rating with a declared tie model and task-aware uncertainty.
- Public result browsing with prompt search, side-by-side artifacts, human highlights, and cost-versus-preference views.

Each issue should state the decision it informs, the single experimental change where practical, the outcome check, and the rough workload. Public voting and live task submission are possible later products. The initial scorer population remains the two maintainers.

## Decisions still needed before paid OrcaBench runs

The exact gateway routes and supported effort settings need a working test. Whole-tree budget, deadline, concurrency cap, task packages, artifact hosting, and confirmation workload need concrete values. This repository's creation did not authorize or perform an OrcaBench run batch.
