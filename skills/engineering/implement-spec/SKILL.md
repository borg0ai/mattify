---
name: implement-spec
description: "Implement a coordinated set of Approved child RFCs from .spec. Use when a multi-part change has an Approved umbrella RFC and approved child RFCs."
disable-model-invocation: true
---

Implement a multi-part change from its Approved umbrella RFC and Approved child RFCs in `.spec/rfc/`.

The umbrella RFC defines the destination and child RFCs define implementation scope. Issue tracker items may supply context, but they are not tasks or authority for implementation. Do not create, update, close, or publish implementation tickets as part of this skill.

## Steps

1. Read the umbrella RFC, its listed child RFCs, and Specify-managed task tracking. Use the host-installed `/specify` skill and its CLI for status and task lifecycle. Do not hand-edit managed status or task files when a command exists.
2. Confirm each child RFC is `Approved`. If a needed child is missing or not approved, stop implementation for that scope and return to `/specify`.
3. Follow explicit dependency and ordering decisions recorded in the RFCs. If order or dependencies are unresolved, ask `/specify` to resolve them; do not infer a parallel task graph from tracker tickets.
4. Implement approved child RFCs one at a time on the current branch. Use `tdd` at the approved behavior seams. Run relevant checks and record truthful results.
5. Review the combined changes with `code-review`, using the umbrella and child RFCs as scope. Fix in-scope findings; send new requirements to `/specify`.
6. Use the host-installed `/specify` workflow to update task tracking and advance RFC statuses only after their acceptance criteria are met. Report completed RFCs and any remaining approved work.

Do not create integration branches, worktrees, or pull requests unless the user or repository workflow explicitly requires them.
