# Agent instructions

Keep work scoped to OrcaBench. LiteBench is a separate project.

## Read for the task

- Before choosing implementation work, read [the roadmap](research/roadmap.md) for the order of work and completion criteria.
- Before implementing an agent runner or testing model routes, read [integrations](research/integrations.md), especially the accounting gap and first integration test criteria. OpenCode JSON stdout alone may omit worker usage.
- Before changing contestant configuration, task packages, judging, scoring, or result publication, read [the evaluation protocol](research/protocol.md). It defines configuration versioning, independent blind votes, separate correctness and preference results, and public evidence.
- Before revisiting a design decision, read [the research history](research/README.md) for the alternatives and reasons behind it.

## Integration work

The first implementation task is a reproducible OpenCode solo/team test. Inspect the working tree, installed CLI version, and available model-route configuration before writing the plan. Read configuration without exposing credentials. Pin the tested version and record a sanitized configuration.

Preserve native orchestration. Follow the integration document's acceptance criteria for route and effort support, tool execution, descendant usage, cancellation, reproducible start states, and external verification. Record failures and missing usage explicitly. Documentation and source inspection establish behavior to test; only execution establishes working route compatibility.

Before paid execution, establish the run scope and resource limits and check the user's existing run authorization. Authorization to edit or publish documentation does not authorize paid runs. Prepare the task, verifier, and concrete run plan before requesting any missing authorization.

## Repository maintenance

Keep the README focused on what the project does and its current status. Keep agent instructions here and detailed experiment requirements in the linked research documents. Derive paths, branch state, installed versions, and available commands from the workspace rather than copying them into instructions.

Use the available `unslop` skill for prose, `writing-for-agents` for agent instructions, and `ponytail` for implementation work.

Publish original research summaries and eligible task artifacts. Keep private chats, private writing prompts and outputs, personal correspondence, credentials, and local credential configuration out of the repository. Use the account's public GitHub noreply identity for commits.

After documentation edits, run `git diff --check` and resolve every local link in changed Markdown files. Report what was verified and distinguish proposed experiments from completed runs.
