# Research and decision history

Research consolidated on September 5, 2026, Europe/Berlin. This is a public summary of the earlier investigation, including proposals that were revised. No OrcaBench experiment has run. A documented capability and a measured working integration are different levels of evidence.

## The question we want to answer

Which complete agent setup would the two maintainers use for a given kind of task, at a given cost and deadline? A second useful question is whether a controller benefits from a particular worker configuration. These questions fit the project's personal scope.

Isolating a harness effect requires stricter matching of models, tools, prompts, settings, environment, and limits across harnesses. Native product comparisons can still be useful when that matching is impossible, provided the result names the whole configuration.

The latest direction makes the maintainers the actual preference scorers. AI may assist with evidence collection or flag candidate issues, but its opinions do not become human votes. Public readers should see the inputs, artifacts, specific objections, and disagreement. The leaderboard describes the maintainers' judgments on the published task mix.

## Recommendations carried forward

Start with OpenCode for the mixed-provider worker experiment, subject to an actual route test. Consider Harbor when its containers and existing adapters save work. Preserve native orchestration behavior. A newly written controller would become another contestant to evaluate.

Freeze contestant versions and task starting states. Collect the whole execution tree, including failed calls and partial runs. A controller reading a worker's output also spends tokens. Cheap workers can increase the controller's work, so worker token prices alone do not predict savings.

Use both solo and same-model team references. Let controllers decline to delegate. Success without workers can be the right behavior on a small task. Compare assigned configurations first, then inspect traces to explain what actually happened.

Separate preference, acceptability, objective correctness, and resource use. A person can prefer one result while finding both unusable. A beautiful screenshot does not establish that a game implements its mechanics.

Spend early effort on distinct tasks and reliable verifiers. Additional votes on the same artifacts measure rater agreement; additional runs measure generation variability. Neither replaces broader task coverage.

## How the plan changed

| Earlier proposal | Current decision and reason |
|---|---|
| A broad orchestration benchmark with solo, naive fan-out, oracle decomposition, and adaptive orchestration | Preserve these as later diagnostic experiments. The first question is which practical configuration the maintainers prefer. Building an oracle decomposition for every task would delay that answer. |
| 12 instances × four orchestration arms × two harnesses × two repeats = 192 runs | Superseded as the initial workload. It isolates more mechanisms but requires two working integrations and much more task preparation. |
| Two harnesses × solo/team × 20 tasks × two repeats = 160 runs | Superseded as the initial pilot. Begin with one harness and verify execution and judging before expanding. |
| One harness, eight configurations, six tasks = 48 runs | Retained as a screening proposal after a two-task integration check. It is not a power calculation or a conclusive leaderboard. |
| Four worker modes per controller: solo, Luna, GLM, mixed Luna/GLM | Replace the mixed pool with a same-model team reference. Add adaptive worker selection once fixed worker choices have a useful baseline. |
| Assume max effort is better, then inspect only cases where high failed | Treat effort as an empirical question. A targeted failure diagnosis is useful, but fresh tasks are needed before claiming a general benefit. |
| One OpenAI-compatible gateway makes every harness comparable | Revised after checking protocols. Responses, Chat Completions, and Anthropic's gateway protocol are distinct. A route must preserve tools and model settings, and might not support native child-provider switching. |
| Five vote choices mixing tie, neither, and cannot judge | Use preference and acceptability as separate fields. Both unacceptable can coexist with a clear preference for A. |
| Fit Elo immediately | Begin with observed comparisons and task outcomes. Later fit batch Bradley-Terry with an explicit tie policy and an optional Elo-like display. |
| Macro-average category Elo values into an overall score | Define the task mix for an overall fit. Independently fitted category ratings do not necessarily share a comparable origin or scale. |
| Hundreds of concurrent runs should be cheap because workers are cheap | Measure inference rate limits, controller overhead, and billing completeness first. Local process count is not provider capacity. |
| Reuse MAFBench as a ready-made solution | Its controlled framework experiments are useful reference material. The inspected paper reports incomplete tool-use evaluation, so it does not establish suitability for this artifact arena. |

Earlier numerical suggestions such as 30 to 50 tasks, 100 task pairs, or three repeats are planning heuristics. Choose confirmation size using observed variability and the smallest difference that would change a practical decision. Do not turn a convenient count into a guarantee.

## Statistical lessons

Blind assignment reduces identity and position bias when presentation is balanced. It does not remove taste, familiarity, attention differences, or preference for attractive but faulty artifacts. Two maintainers can produce a useful personal benchmark; they do not represent a population of all users.

Even 14 wins in 20 independent binary comparisons has an approximate 95% Wilson interval of 48% to 85%. Votes on a few shared tasks contain less independent information than that example assumes. Show distinct tasks, attempts, and ballots separately.

Best-of-many selection favors configurations with more attempts or tuning choices. Keep exploratory results visible, freeze finalists, and use fresh tasks for confirmation. Repeating the same small task set mainly measures repeatability on those tasks.

Preserve task blocks when estimating uncertainty. With two raters, show each rater's outcomes and their disagreement rather than implying robust population-level voter uncertainty. Bradley-Terry needs a connected comparison graph; sparse or fully separated outcomes require careful handling. Keep direct pairwise outcomes visible when preferences are nontransitive.

## Related work and what to borrow

These sources informed the investigation. A paper's result supports the claim tested in that paper; it does not validate OrcaBench's future scores.

| Source | Useful contribution | Limit for this project |
|---|---|---|
| [Chatbot Arena](https://arxiv.org/html/2403.04132v1) | Anonymous comparisons, batch Bradley-Terry, sampling and uncertainty | Its population and interaction mix differ from two maintainers judging coding artifacts. |
| [Code Arena](https://arena.ai/code) and [how it works](https://arena.ai/how-it-works) | Prompt, anonymous artifacts, vote, then reveal | Public live execution and community voting are beyond the initial scope. |
| [MT-Bench](https://arxiv.org/abs/2306.05685) | Position, verbosity, and self-preference issues in model judges | OrcaBench's preference score will come from people. Human bias still needs consideration. |
| [MultiAgentBench](https://arxiv.org/html/2503.01935v1) | Coordination structures, milestones, communication analysis | Activity and communication ratings should explain outcomes rather than determine the main score. |
| [MAFBench](https://arxiv.org/html/2602.03128) | Controlled comparisons of multi-agent frameworks | The inspected tool-use evaluation is incomplete. Test adapters before adopting them. |
| [Magentic-One and AutoGenBench](https://arxiv.org/abs/2411.04468) | Manager-specialist execution, isolated repetitions, ablations | A framework benchmark addresses a different comparison from native product use. |
| [SWE-bench](https://arxiv.org/abs/2310.06770) | Real repository issues and executable verification | Reused tasks bring licensing, contamination, dependency, and test-quality considerations. |
| [AppWorld](https://arxiv.org/abs/2407.18901) | Final-state checks and collateral effects | Its environment needs adaptation for coding artifacts. |
| [τ-bench](https://arxiv.org/abs/2406.12045) | State-based validation and repeated-success reliability | Reliability requires repeated attempts; one result per task is insufficient. |
| [AgentDojo](https://arxiv.org/abs/2406.13352) | Separate benign utility, utility under attack, and attack success | Introduce fault and injection variants only after a clean baseline works. |
| [OpenTelemetry GenAI conventions](https://github.com/open-telemetry/semantic-conventions-genai) | Existing vocabulary for model/tool traces | Native records may need explicit parent, join, and message links. A telemetry migration is not needed for the first run. |
| [OpenAI Agents SDK](https://openai.github.io/openai-agents-python/multi_agent/) | Distinct manager-as-tool and handoff patterns | Building a controller with the SDK evaluates that controller; it does not reproduce Codex's native orchestration. |
| [Inspect multi-agent evaluation](https://inspect.aisi.org.uk/multi-agent.html) | Evaluation infrastructure and simple baselines | Its model bridge can change generation settings unless configured to forward them. |

The earlier writing-benchmark research supplied one transferable lesson: a score needs an explicit meaning and inspectable evidence. [FLASK](https://arxiv.org/abs/2307.10928), [WritingBench](https://arxiv.org/html/2503.05244v4), and [LitBench](https://aclanthology.org/2026.eacl-long.362/) discuss criteria and human preferences. [PoLL](https://arxiv.org/abs/2404.18796) studies panels of model judges. More judges alone do not establish a common scale. [UniversalCEFR](https://arxiv.org/html/2506.01419) illustrates how two similar-sounding evaluation targets, audience accessibility and writer proficiency, can differ. Those writing-specific scorers are outside OrcaBench's scope.

Implementation sources and a dated price snapshot are in [integrations](integrations.md). The operative experiment proposal is in [protocol](protocol.md); this file preserves the reasoning and superseded alternatives.
