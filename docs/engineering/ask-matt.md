## What it does

`ask-matt` routes work through Mattify's RFC-first skill map. For product, behavior, architecture, or code changes, host-installed `/specify` owns RFC creation, validation, and approval. Supporting skills clarify decisions or gather evidence; implementation starts only from an Approved RFC.

## When to reach for it

You invoke this by typing `/ask-matt`; the agent won't reach for it on its own. Use it when you want help choosing a Mattify skill or workflow. For direct RFC lifecycle work, use the host-installed `/specify` skill.

## Where it fits

This is the user-invoked router over the skill set. It directs decision discovery to skills such as [grill-with-docs](../../skills/engineering/grill-with-docs/SKILL.md), RFC work to host `/specify`, and approved implementation to [implement](../../skills/engineering/implement/SKILL.md). It also routes unrelated tasks to standalone utilities when no RFC is needed.

## Common questions

**Does Mattify ship `/specify`?**

No. Install the host-provided `specify` skill separately. Mattify routes to it and does not implement a second RFC lifecycle.

**Can an issue or ticket authorize implementation?**

No. Tracker items provide context. An Approved RFC defines scope and approval.

## It's working if

- Each project change routes through host `/specify` before implementation.
- Supporting skills contribute evidence or decisions without creating another approval path.
- Standalone utilities remain available for requests that do not propose project changes.
