## What it does

`implement-spec` coordinates implementation across an Approved umbrella RFC and its Approved child RFCs. Each child RFC defines a bounded part of the work, while the umbrella records the overall destination.

RFC hierarchy and Specify-managed task tracking remain the authority. Issue tracker tickets are context only; this skill creates no parallel implementation graph.

## When to reach for it

You invoke this by typing `/implement-spec`, and the agent won't reach for it on its own. Reach for it when one change has multiple independently reviewable Approved child RFCs. For one small RFC, use [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md). If a child is missing or unclear, return to the host-installed `/specify` skill.

## Prerequisites

An Approved umbrella RFC and Approved child RFCs must exist under `.spec/rfc/`. The host must provide `/specify` for status and task tracking.

## Child RFCs are the work units

Implementation follows dependency and ordering decisions recorded in RFCs. The skill does not infer dependencies from issue tracker relationships or start parallel work based on guessed file overlap. Unresolved ordering returns to `/specify`.

## Common questions

**Can it use existing tracker tickets as the task graph?**

No. Tickets may add context, but they cannot define implementation scope or dependencies. Use `/specify` to settle the RFC hierarchy and task order.

## It's working if

- Every implemented child is Approved and linked from the umbrella RFC.
- Work order follows recorded decisions, not guessed tracker dependencies.
- Combined review checks all changes against the umbrella and child RFCs.
- Specify-managed tracking changes only through the `/specify` workflow.

## Where it fits

`implement-spec` builds an approved multi-RFC effort. [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) handles a single RFC; [tdd](https://github.com/borg0ai/mattify/blob/main/skills/engineering/tdd/SKILL.md) guides test-first slices, and [code-review](https://github.com/borg0ai/mattify/blob/main/skills/engineering/code-review/SKILL.md) checks the combined result. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
