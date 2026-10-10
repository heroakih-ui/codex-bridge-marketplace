---
name: check
description: Verify that Claude Code can find and authenticate the local Codex CLI and receive a real response.
disable-model-invocation: true
---

Read `${CLAUDE_PLUGIN_ROOT}/references/workflow.md` and follow it.

Report the current shell environment and working directory, the located Codex executable, its version, and login status without displaying secrets. Then run a single ephemeral read-only Codex request in the current directory: "Connectivity check only. Do not read project files, run commands, or modify files. Reply with CODEX_BRIDGE_OK." Use the workflow's invocation pattern and the non-Git exception only if needed.

Report success only if the process exits successfully and its final response contains CODEX_BRIDGE_OK. Distinguish CLI discovery, authentication, and inference results. If a prerequisite is missing or execution fails, give the actual failure and the next necessary step. Answer in the user's language.
