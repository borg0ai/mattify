## What it does

`wayfinder` helps make a large, uncertain effort legible before RFCs are written. It maps the destination, decisions, dependencies, and unknowns in the conversation, then hands the settled structure to the host-installed `/specify` skill.

It creates no tracker map or decision tickets. `/specify` alone creates and manages the umbrella and child RFCs that define project scope.

## When to reach for it

You invoke this by typing `/wayfinder`, and the agent won't reach for it on its own. Reach for it when the destination is known but decisions span multiple sessions. If the work is already clear and small, ask `/specify` to author one RFC directly. If an Approved RFC already exists, use [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md).

## Destination and unknowns

The **destination** is the outcome the RFC set must enable. The **unknowns** are facts or decisions still needed to write it. Keeping those separate prevents an open question from turning into an implementation commitment.

Wayfinder presents the map for discussion. The user settles decisions; `/specify` records RFCs and owns their status and task tracking.

## Common questions

**Does wayfinder create the RFC hierarchy?**

No. It organizes the discussion and recommends a split. The host-installed `/specify` skill creates, validates, and tracks the umbrella and child RFCs.

## It's working if

- The destination and remaining decisions are clear before RFC authoring.
- Facts are distinct from assumptions and unresolved questions.
- No tracker map, decision ticket, or implementation ticket is created.
- The handoff uses `/specify`; implementation waits for Approved RFCs.

## Where it fits

`wayfinder` is a discovery step before RFC authoring with the host-installed `/specify` skill, useful when one conversation cannot settle the design. [triage](https://github.com/borg0ai/mattify/blob/main/skills/engineering/triage/SKILL.md) brings in outside reports; [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) starts only after approval. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
