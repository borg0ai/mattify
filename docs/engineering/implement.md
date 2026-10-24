## What it does

`implement` turns one Approved RFC into code. The RFC under `.spec/rfc/` is the complete scope; tickets, issues, and conversation can add context but cannot add requirements.

It stops when the RFC's acceptance criteria are met, relevant checks are reported truthfully, and review findings are resolved. Status and task tracking go through the host-installed `/specify` skill.

## When to reach for it

You invoke this by typing `/implement`, and the agent won't reach for it on its own. Reach for it when one Approved RFC describes a change small enough for one implementation run. If it spans several approved child RFCs, use [implement-spec](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement-spec/SKILL.md). If scope is missing or unclear, use the host-installed `/specify` skill first.

## Prerequisites

The repository must contain an Approved RFC for the requested change, and the host must provide `/specify` for RFC status and task tracking.

## Scope stays fixed

`implement` builds settled decisions. Any new requirement returns to `/specify`; it does not grow from an issue comment, a failing test, or a code review suggestion.

## Common questions

**Can I point it at a ticket instead of an RFC?**

A ticket can help locate the request or provide evidence. It cannot authorize implementation. Use `/specify` to record and approve the scope first.

## It's working if

- The session names the Approved RFC and its acceptance criteria before editing.
- Every implemented behavior traces to that RFC.
- Checks and review results are reported as actually observed.
- Scope questions return to `/specify` instead of being guessed.

## Where it fits

`implement` is the build step after RFC approval. [tdd](https://github.com/borg0ai/mattify/blob/main/skills/engineering/tdd/SKILL.md) guides behavior tests, and [code-review](https://github.com/borg0ai/mattify/blob/main/skills/engineering/code-review/SKILL.md) checks the result against the same RFC. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
