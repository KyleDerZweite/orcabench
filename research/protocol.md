# Evaluation protocol proposal

Status: WIP, unexecuted. Freeze a numbered protocol before measured runs. Record any later correction and its effect on which results remain comparable.

## What competes

A contestant is a complete, versioned configuration:

`harness/version + controller/effort + worker policy + prompts/skills + tools/environment + resource limits`

A worker has an independent context, its own model session, a role, tools, and a parent relationship. Repeated calls inside the controller context are ordinary model calls. Store both kinds accurately.

Task snapshots, attempts, and their identifiers belong to runs. A changed skill, route, model setting, or worker policy creates a new contestant version. Record explicit model IDs rather than relying on display names. Preserve native delegation decisions.

## First measured screen

Use one verified OpenCode integration. The proposed configurations are:

| Controller | Worker modes |
|---|---|
| Astra high | Solo; Astra workers; Luna workers; GLM workers |
| Fable 5.1 high | Solo; Fable workers; Luna workers; GLM workers |

Choose supported worker effort settings during integration, record them, and freeze them before the screen. An unsupported setting must remain an explicit limitation. The adaptive Luna/GLM pool is a later contestant.

Every configuration receives the same whole-tree cost ceiling, wall-clock deadline, and concurrency ceiling. Freeze their actual values before running. Record the resources used and whether any limit was reached. These constraints define the practical experiment; they do not imply equal consumed compute.

Start with two tasks to prove execution, verification, artifact capture, and accounting. Expand to six prepared tasks once those checks pass:

| Task | Evidence required |
|---|---|
| Deceptively simple repair | A small executable check, appropriate edit scope, and preserved existing behavior |
| Real repository bug | Frozen issue and repository state, reproducer, repair checks, and regression checks |
| Change across files or packages | Requirement coverage and checks that cross component boundaries |
| Bounded tower-defense feature | Fixed replay inputs and assertions for placement, currency, damage, waves, and restart as relevant to the brief |
| Request contradicted by a supplied API contract | Correct identification of the contradiction, evidence, and an appropriate bounded response |
| Feasible counterpart to the API task | Successful implementation so blanket refusal does not appear effective |

The table proposes task types, not finished task packages. Write unambiguous briefs, retain editable artifacts, and run verifiers outside the agent's writable environment. An API task must include enough information to establish the contradiction. A vaguely impossible task cannot distinguish justified caution from failure.

Six tasks × eight configurations = 48 runs. Randomize execution order within task blocks where practical. Run each from a clean snapshot. Retain failed and timed-out attempts. Separate infrastructure failures from agent outcomes and apply a declared rerun rule consistently.

A planned 48 comparisons would require 96 ballots if both maintainers review each pair. This is a workload option, not a requirement to compare every pair. Keep comparison coverage connected, balance left/right assignment, and include the planned solo/team and worker comparisons. Publish the pair-selection rule and any omissions.

## Human judging

Each maintainer votes independently before seeing the other's vote. Give both the same prompt, artifact presentation, and verification evidence. Hide configuration identity, cost, latency, existing ratings, and execution traces until a ballot is recorded. Review actual artifacts or standardized replays where possible.

Record:

- Preference: A, B, tie, or cannot judge.
- Acceptability of A: acceptable, unacceptable, or cannot judge.
- Acceptability of B: acceptable, unacceptable, or cannot judge.
- A short reason, with a quote, file location, screenshot region, or replay event when an objection has specific evidence.

For the initial protocol, show standardized verifier results before voting and describe the question as an informed shipping preference: "Which result would you use for this task?" Record this presentation policy. A later aesthetic-only condition would need its own protocol.

Allow both artifacts to be unacceptable while A is preferred. Do not rewrite a human preference because a test failed. Tests and votes answer different questions, and the reader should see both. Keep each maintainer's ballot, including disagreement. Store corrections as explicit revisions with reasons.

Before the measured batch, use a few practice comparisons to find confusing criteria and broken artifact previews. Freeze the judging guidance after that practice. A practice vote does not belong in the reported measured batch.

## Results and scoring

Initially report observed A/B/tie outcomes, acceptability rates, verified task outcomes, and per-task evidence. If a summary preference percentage is useful, define it explicitly, for example `(wins + 0.5 × ties) / judged comparisons × 100`. Exclude cannot-judge ballots and display their count. Label it as a descriptive share on the sampled comparisons, not a probability of succeeding on future work. Opponent mix affects it.

Later fit Bradley-Terry in batches when there is enough connected coverage. Decide the tie treatment before fitting, with a tie model if the data support it. An Elo-like display can be a declared transformation of the fitted strength, for example `1000 + 400 / ln(10) × centered log-strength`. Publish the centering rule, estimation method, and model version. The value is a relative preference rating and is not a percent.

Always expose distinct task count, attempt count, ballot count, pair coverage, ties, abstentions, and per-rater results. Preserve task blocks for uncertainty estimates. Sparse tasks and two raters limit the claims an interval supports. Do not average independently fitted category Elo values. Define the task distribution for any overall fit and retain category outcomes alongside it.

Report correctness using external checks and requirement coverage. Single-attempt success is useful once each task has a declared success condition. `pass@k` asks whether at least one of k attempts succeeds; `pass^k` asks whether all k succeed. Best-of-many success does not establish single-run reliability. Use repeated-run estimators only when the recorded attempts support them and publish the estimator.

Report cost and runtime separately. Show whole-system cost with the price source and completeness, controller and worker usage where available, actual elapsed time, limit hits, and failed attempts. Cost per successful task must include failed attempts in the numerator and declare which attempts enter the denominator. Missing cost is unknown, not zero.

## Public evidence and storage

Use simple records and artifact files until an actual workflow needs a database. The essential records are contestant version, task version, run, artifact, verification result, comparison, ballot, and trace reference. Stable identifiers and hashes connect them.

Every run should preserve the prompt, starting snapshot identifier, configuration, requested and returned model IDs, artifact hashes, completion or failure status, retry history, timestamps, and usage completeness. Retain raw provider receipts privately when they contain sensitive metadata, and publish a redacted accounting summary. Hidden reasoning text is not required.

Public readers should see the full publishable input, outputs, verifier method and results, human ballots and highlighted concerns, configuration, and resource data. Keep credentials, private source material, personal information, and unsafe executable previews out of the public bundle. If a task must remain withheld, say so and describe what readers cannot independently inspect. Public task release after a season needs fresh held-out tasks for subsequent confirmation.

A future trace view can show spawns, messages, waits, joins, cancellations, retries, tool actions, and artifact lineage. It should explain a result. More agent activity does not earn preference points.

## Confirmation and later experiments

Select finalists from the screen, freeze them, and run fresh tasks. Choose the number of tasks and repetitions from the observed variability and the smallest practical difference worth detecting. Report the selection procedure so exploratory winners are distinguishable from confirmed results.

Introduce one controlled change at a time: high versus max, a skill present versus absent, fixed versus adaptive worker choice, or clean versus faulty worker reports. For faults, specify a reproducible intervention such as a timeout, stale claim, contradiction, or injected instruction. Compare task utility and recovery against the clean condition.

Blender belongs in a separate track once scene loading, editable artifact collection, rendering, and checks are reliable. Use geometric checks and a standardized render or animation. Research dossiers, data audits, constraint scheduling, oracle decomposition, and nested delegation remain useful later task families or experimental conditions.
