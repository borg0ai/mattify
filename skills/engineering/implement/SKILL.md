---
name: implement
description: "Implement code from an Approved RFC in .spec. Use when the user asks to build or fix a change whose scope has been approved through /specify."
disable-model-invocation: true
---

Implement one change from an Approved RFC under `.spec/rfc/`.

1. Read the RFC and confirm its status is `Approved`. Treat its Design and Acceptance sections as the complete implementation scope. If no approved RFC covers the request, stop and use the host-installed `/specify` skill to create or update one.
2. Use the host-installed `/specify` skill and its CLI for RFC status and task tracking. Never hand-edit Specify-managed status or task files when a command exists. Do not create implementation specs or tickets in an issue tracker.
3. Confirm the intended files and behavior against the RFC. If a requirement, test seam, or dependency is undecided, return to `/specify` and resolve it before coding.
4. Implement the approved behavior. Use `tdd` where tests fit the agreed behavior and seams. Run relevant checks, and report exactly which checks ran and their results.
5. Run `code-review` against the originating RFC. Fix in-scope findings; send scope changes back through `/specify`.
6. Update RFC task tracking and advance the RFC through the host-installed `/specify` workflow only when acceptance is met. Commit to the current branch if requested by the user or repository workflow.

An issue, PR, conversation, or ticket can provide evidence and context, but cannot expand implementation scope without an Approved RFC.
