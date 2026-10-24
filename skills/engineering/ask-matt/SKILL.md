---
name: ask-matt
description: Route ideas, requests, and code changes through Mattify's RFC-first workflow, with /specify as the canonical RFC lifecycle entry.
disable-model-invocation: true
---

# Ask Matt

You do not need to remember every skill. Ask which path fits, then read each recommended skill's `SKILL.md` before describing its behavior or skipping a step.

## The rule

For project work that changes code, behavior, architecture, or product decisions, `/specify` owns the RFC lifecycle. Use it to create and validate the RFC, record the user's decision, and keep RFC status and indexes in sync. `/specify` is provided by the host harness; do not look for or copy its implementation into this repository.

Other skills can investigate, clarify, prototype, or record decision input for an RFC. They do not create a parallel spec or authorize implementation. Start implementation only from an Approved RFC. A ticket, issue, conversation, or prototype is not an alternate specification or approval path.

## The main flow: idea to approved RFC to implementation

1. **Clarify the problem.** For a project in a working directory, use `/grill-with-docs` to resolve decisions and maintain the project's glossary and ADRs. Use `/grill-me` when there is no project directory. Use `/to-questionnaire` when a decision depends on another person's answer. These produce input for the RFC, not a competing spec.

2. **Gather evidence when needed.** Use `/research` for cited primary-source investigation. Use `/diagnosing-bugs` to establish a failing feedback loop and identify a bug. Use `/prototype` to answer a design question that is hard to settle on paper. Use `/domain-modeling` to clarify domain terms and durable decisions. Bring useful findings into the RFC; none of these skills approves implementation.

3. **Create and manage the RFC with `/specify`.** Deliver one RFC per concern. Split a theme into an umbrella and child RFCs when needed. Validate the RFC and keep its status and indexes synchronized with `/specify`. Present the implementation plan and wait for an explicit approval outcome. Rejected or pending RFCs do not proceed to implementation.

4. **Implement only an Approved RFC.** Use `/implement` with the Approved RFC as the implementation source. Drive code changes with `/tdd`; use `/code-review` to compare the result with the Approved RFC and project standards. Do not derive implementation authorization from issue or ticket status. `/implement-spec` currently requires a tracker-published spec and ticket graph, so it is not part of this RFC flow.

5. **Close the work.** Use `/pr` when preparing a pull request and `/retro` to improve the agent environment after the work. Before committing RFC changes, run `/specify`'s consistency check.

## Other work

Some skills are useful without creating or implementing an RFC. Keep them on their actual task boundaries:

- `/triage` organizes incoming reports. If a report calls for a project change, route the proposed change through `/specify` before implementation.
- `/improve-codebase-architecture` identifies improvement candidates. Take a chosen project change to `/specify` before implementation.
- `/codebase-design` provides vocabulary and methods for shaping module boundaries; use its decisions as RFC input.
- `/handoff` moves context between sessions or people. It does not replace an RFC or its approval.
- `/teach`, `/wait-what`, `/writing-for-agents`, and `/wizard` handle learning, clarification, agent-facing writing, and human-only setup tasks. They can remain standalone when no project change is being proposed.
- `/grilling` is the interview primitive used by higher-level flows. Prefer its named wrappers unless the user explicitly wants the primitive.

Do not route users to `/to-spec`, `/to-tickets`, or `/wayfinder` as alternate planning or implementation entry points. They publish tracker specs or decision tickets outside `/specify`'s RFC lifecycle. Do not tell users to run the upstream setup command as a prerequisite for Mattify's RFC workflow; use `/setup-mattify-skills` only to check repository setup.

## Context boundaries

Use [PHASE-BOUNDARIES.md](PHASE-BOUNDARIES.md) when deciding whether to continue, clear, hand off, delegate, or compact at a phase boundary. Preserve the RFC and its approval decision across any context transition. Never use a context transition to bypass the Approved RFC gate.

## Before routing

Check the user's actual goal. If they ask for information, learning, or a human-only setup task, answer with the relevant standalone skill. If they propose changing a project, identify which clarification or evidence skills help, then make `/specify` the RFC entry and require Approved status before implementation. If the change is already covered by an Approved RFC, route to the implementation skill that matches its scope.
