---
name: review
description: Ask Codex for a read-only review of the current project or specified changes, and assess its findings.
argument-hint: "[review scope or question]"
---

Read `${CLAUDE_PLUGIN_ROOT}/references/workflow.md` and follow it.

User scope: $ARGUMENTS

Find the actual project root and applicable project instructions. Default to reviewing the current uncommitted changes if the user did not specify another scope. Inspect Git status to establish that scope; if no changes exist, ask for the intended review target.

Send Codex the review scope, relevant context and absolute project path. Run with the read-only sandbox. Request actionable bugs with file locations, severity, concrete triggering conditions, and evidence. Explicitly forbid edits. Do not send credentials or unrelated private files.

Assess the returned findings against the actual code. Report supported findings in the user's language and mark uncertainty. Do not say the review passed if the process failed. Do not modify files merely because the review suggests a fix.
