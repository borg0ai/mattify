## What it does

`triage` analyzes incoming reports and pull requests, checks claims against available evidence, and recommends what should happen next. It separates intake from product scope: a report does not authorize implementation.

An accepted product change goes through the host-installed `/specify` skill and becomes an RFC in `.spec/`. Triage does not publish specs, implementation tickets, or agent briefs to issue trackers.

## When to reach for it

You invoke this by typing `/triage`, and the agent won't reach for it on its own. Reach for it when an incoming bug, enhancement, or external PR needs evaluation. For accepted product work, use `/specify` to settle and approve scope before implementation.

## Evidence before recommendation

The useful output is a grounded recommendation: what is already known, what was verified, and what decision remains. Triage can continue using configured tracker labels and comments for intake status, but those artifacts never replace an Approved RFC.

## Common questions

**If a report is ready for an agent, can implementation start?**

Only after the relevant RFC is Approved. `ready-for-agent` is an intake signal; `/specify` owns product scope and approval.

## It's working if

- The claim is checked against code or a reproducible report before recommendation.
- Facts, unknowns, and recommendation are easy to distinguish.
- Accepted product work is handed to `/specify`, with no new tracker ticket or agent brief.
- No implementation begins without an Approved RFC.

## Where it fits

`triage` is an intake path into RFC authoring, not a parallel planning chain. [wayfinder](https://github.com/borg0ai/mattify/blob/main/skills/engineering/wayfinder/SKILL.md) helps when the decision space is large; [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) builds only after approval. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
