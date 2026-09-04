# OrcaBench

![An orca swimming above a quiet teal sea](assets/orca.svg)

## WIP

OrcaBench is a personal orchestration benchmark. Two maintainers compare anonymous results from coding agents and their subagents, record what they would use, and explain their choices. Public readers will be able to inspect the task, both artifacts, checks, and the reasons behind a rating, then make their own judgment.

We want to find configurations we would actually use on our projects. The eventual leaderboard will reflect our tasks and preferences. Human votes are the authority for preference scores. Automated checks report whether the result works; cost and runtime show what it took.

This repository currently contains research, a proposed evaluation protocol, and an orca design reference. No benchmark runs, ballots, ratings, or working arena have been produced here.

## Start here

- [Research and decision history](research/README.md): findings, earlier proposals, and what changed.
- [Evaluation protocol](research/protocol.md): contestants, tasks, blind judging, public evidence, and score interpretation.
- [Harnesses, model routes, and costs](research/integrations.md): documented capabilities, accounting gaps, and the first integration test.
- [Roadmap](research/roadmap.md): small steps with concrete completion criteria and a backlog for future issues.
- [Agent handoff](.scratch/handoffs/20260904T222714Z-orcabench.md): the current workspace and the next action.

The proposed first experiment uses one harness, two controller models, and four worker configurations per controller. Six tasks would produce 48 runs. That is a screening exercise. A later confirmation batch needs fresh tasks.

## What readers should see

Start with the prompt and actual result. Let readers inspect a diff, run an artifact where practical, and read our quoted or highlighted objections. A percentage or rating should be a route into the evidence, never the only thing on the page.

The public result view should expose each maintainer's preference and acceptability decision, disagreements, verifier outcomes, the exact configuration, cost completeness, and task coverage. During judging, identity and resource consumption stay hidden until the vote is recorded.

Initial publication can use static pages and precomputed results. A small private ballot workflow is enough for two scorers. Public accounts, live task submissions, and a production execution queue can wait until they solve a demonstrated problem.

## Design reference

The orca is the visual reference: a clear black silhouette, white eye patch and belly, and a small amount of sea color. The original [SVG](assets/orca.svg) is included under this repository's MIT license.

| Use | Color |
|---|---|
| Ink and orca | `#101820` |
| Page background | `#FAFCFC` |
| White markings | `#FFFFFF` |
| Sea accent and links | `#086F73` |
| Pale sea panels | `#DDEEEF` |

Use plain labels alongside color for pass, failure, disagreement, and missing data. Keep the mascot out of the artifact comparison area. The work being judged should get the space.

## Ideas and scope

[Open an issue](https://github.com/KyleDerZweite/orcabench/issues) for a task proposal, measurement problem, integration finding, or controlled experiment. Include the decision the idea would help us make and how we could check the outcome. The [roadmap](research/roadmap.md) lists current candidates; they are proposals rather than promises.

OrcaBench grew out of the research for [LiteBench](https://github.com/KyleDerZweite/litebench), a separate personal writing benchmark. This project focuses on complete agent configurations and human comparison of their artifacts.

The name is already used by the unrelated [Airoura/OrcaBench](https://github.com/Airoura/OrcaBench), which studies social AI character content. This repository is an independent orchestration project and claims no affiliation or name exclusivity.

## License

[MIT](LICENSE). Linked papers, software, and websites retain their own licenses. This repository summarizes research in original prose and does not redistribute private chats or third-party datasets.
