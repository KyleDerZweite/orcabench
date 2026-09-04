# Harnesses, model routes, and costs

Status checked September 5, 2026, Europe/Berlin. The sources below establish documented behavior or inspected code. This repository has not executed any of these integrations with the intended model routes.

## Preferred first integration

OpenCode is the first candidate because its [agent configuration](https://opencode.ai/docs/agents/) supports per-agent `provider/model-id` selection. Run the native agent with its normal delegation tools. Collect native session records and final artifacts with a small wrapper.

Use [Harbor](https://harborframework.com/docs/agents) if its task containers, verification, and agent adapters remove work. Its current accounting path needs attention before running a team benchmark. Avoid adding a second evaluation runner to the same initial path without a concrete need.

| Candidate | Evidence from research | Integration still to establish |
|---|---|---|
| OpenCode | [Agent docs](https://opencode.ai/docs/agents/) describe agent models in `provider/model-id` form. [Server docs](https://opencode.ai/docs/server/) expose sessions, children, and messages. | Exact controller and worker routes, supported efforts, complete child collection, and cancellation behavior. |
| Codex CLI | [Configuration reference](https://developers.openai.com/codex/config-reference) covers model providers and agent roles. The investigated provider path requires Responses compatibility. | Native per-child provider switching was not established by the inspected role implementation. Do not infer it from a child model override. |
| Claude Code / Agent SDK | [Gateway protocol](https://code.claude.com/docs/en/llm-gateway-protocol) and [subagent docs](https://code.claude.com/docs/en/agent-sdk/subagents) describe their supported interfaces. | Arbitrary OpenAI-compatible JSON is insufficient. Verify actual model routes and tools; use a native configuration comparison where matching is unavailable. |
| Harbor | Existing installed-agent adapters and container task infrastructure. | Complete worker accounting for the selected adapter, task dependency setup, and verifier isolation. |
| Inspect | [Agent bridge](https://inspect.aisi.org.uk/agent-bridge.html) can capture model calls and connect agent execution to evaluation. | Generation settings are dropped by default. Explicitly configure forwarding when the native agent's settings must remain authoritative. |

Native LangGraph, AutoGen, or Agents SDK controllers remain possible contestants. They are not mandatory adapters for the first screen. Comparing a rewritten controller against a native product measures the rewritten controller too.

## Confirmed accounting gap

At OpenCode commit [`5cf9f517cfec3ef68d3e68a12a6a4b3163947f44`](https://github.com/anomalyco/opencode/blob/5cf9f517cfec3ef68d3e68a12a6a4b3163947f44/packages/opencode/src/cli/cmd/run.ts), CLI event handling filters message parts to the parent session. Child message events therefore do not all appear in ordinary JSON stdout.

At Harbor commit [`5c364a538e0af19eb58a53fdb895d7c0f974cef5`](https://github.com/harbor-framework/harbor/blob/5c364a538e0af19eb58a53fdb895d7c0f974cef5/src/harbor/agents/installed/opencode.py), the OpenCode adapter parses stdout and sums `step_finish` usage and cost. That pair of implementations is insufficient evidence of complete team usage. Both relevant source paths were rechecked during this repository's creation. Recheck pinned versions before implementation.

Collect the full descendant tree through native session records or the documented session API, then reconcile totals against provider records where available. Include controller, workers, nested children, retries, partial calls, and canceled work. Deduplicate by stable call identity when combining cumulative and per-call usage.

Claude's [cost tracking documentation](https://code.claude.com/docs/en/agent-sdk/cost-tracking) makes a related distinction. Per-turn main-agent usage excludes subagents, while result `modelUsage` and `total_cost_usd` cover the call's accumulated model usage including subagents. Dollar totals are estimates. Use the documented cumulative semantics rather than summing repeated cumulative totals.

Inspect's [generation configuration section](https://inspect.aisi.org.uk/agent-bridge.html#generation-config) says the bridge drops client sampling and reasoning settings by default, while forwarding structural request settings. Use `forward_generation_config=True` only when those client settings are intended to control the actual served model, then verify the resulting requests.

## Public price snapshot

USD per million tokens, from direct-provider documentation checked on September 5, 2026, Europe/Berlin. These are ordinary input and output rates for the stated conditions. They are not a quote for an intermediary gateway.

| Model | Public API ID | Input | Output | Conditions and source |
|---|---|---:|---:|---|
| Astra | `gpt-6-astra` | $10 | $50 | Standard short-context rates, [OpenAI pricing](https://developers.openai.com/api/docs/pricing) |
| Luna | `gpt-5.6-luna` | $0.20 | $1.20 | Standard short-context rates, [OpenAI pricing](https://developers.openai.com/api/docs/pricing) |
| Fable 5.1 | `claude-fable-5-1` | $10 | $50 | [Anthropic model overview](https://platform.claude.com/docs/en/models/overview) |
| GLM-5.3-Flash | `glm-5.3-flash` | $0.075 | $0.25 | Promotional rates, [Z.ai pricing](https://docs.z.ai/guides/overview/pricing) |

GLM's published list prices are $0.15 input and $0.50 output. The 50% promotion ends September 9, 2026, at 24:00 UTC+8. Cache rates, cache writes, long-context pricing, service tiers, batch modes, tools, and route fees can change a run's cost. Freeze a dated route-specific price snapshot when running. Preserve historical costs instead of silently repricing old results.

The spelling `z-ai/glm-5.3-flash` is a gateway identifier used in the earlier writing experiment. It is not the direct-provider model ID. Astra's tool-calling path requires Responses compatibility, as described in its [model documentation](https://developers.openai.com/api/docs/models/gpt-6-astra). Generic Chat Completions support is not sufficient.

The prior writing experiment estimated about $2.93 for retained generation responses and $21.41 for retained evaluation responses. Those figures illustrate that judging can dominate a writing experiment's spend. They are historical estimates from a different project, omit failed retry usage, and are not an OrcaBench coding-run budget.

## First integration test

Pin the selected OpenCode version and record its configuration. Use a tiny disposable coding task with a known verifier. The test is complete when the evidence shows all of the following:

1. A requested controller and child model both run through the intended routes, with returned model IDs or other provider evidence and no silent fallback.
2. Tools execute correctly and the requested supported effort settings survive the route.
3. Controller and child sessions can be traversed, their artifacts retained, and their usage collected without double counting.
4. A controlled timeout or cancellation leaves a terminal status, partial usage, and recoverable artifact evidence.
5. Two runs start from the same task state and an external verifier checks the result.
6. Estimated cost reconciles with available provider records, or explicitly records the unresolved difference and missing fields.

Do a solo and a team attempt before selecting the full experiment budget. Increase concurrency gradually while recording rate limits and retry overhead. Complete route compatibility, budget values, and task packaging remain open work.
