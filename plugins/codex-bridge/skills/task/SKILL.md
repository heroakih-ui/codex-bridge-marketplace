---
name: task
description: Delegate a user-requested bounded implementation task to local Codex, then inspect and validate the changes.
argument-hint: "<implementation request>"
disable-model-invocation: true
---

Read `${CLAUDE_PLUGIN_ROOT}/references/workflow.md` and follow it.

Implementation request: $ARGUMENTS

If no implementation request is present, ask the user for it. Establish the actual project root, applicable instructions, current Git status, task boundaries, and acceptance criteria from the user's request and session. Ask only when necessary information is missing.

Run Codex with workspace-write for that project. Include the requested task, relevant session context, existing user changes to preserve, allowed files/scope, and required validation in the stdin request. Forbid commits, pushes, destructive operations, publication, and unrelated changes. Do not edit the delegated files while it runs.

After completion inspect the diff and run appropriate checks. Present the final outcome and validation in the user's language, distinguishing Codex's report from what you verified. If the process fails, inspect any partial changes and report them; do not reset or delete them automatically.
