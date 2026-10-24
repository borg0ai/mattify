## What it does

`to-tickets` turns an Approved RFC into a dependency-ordered set of independently verifiable implementation slices. The RFC remains the authority for scope and decisions, and this skill never publishes duplicate issues.

## When to reach for it

You invoke this by typing `/to-tickets`; the agent won't reach for it on its own. Use it when Approved RFC work spans multiple sessions or needs explicit implementation sequencing. If no Approved RFC exists, use host-installed `/specify` first.

## Where it fits

This is an optional implementation planning step after RFC approval. It hands any `.spec/TASK_TRACKING.md` updates to `/specify` and does not authorize implementation by itself. Use [implement](../../skills/engineering/implement/SKILL.md) for one RFC or [implement-spec](../../skills/engineering/implement-spec/SKILL.md) for a larger delivery. The [ask-matt](../../skills/engineering/ask-matt/SKILL.md) router maps the full skill set.

## Common questions

**Can I use it before an RFC is approved?**

No. Create and approve the RFC with `/specify` first.

**Does this publish tickets to an issue tracker?**

No. It produces an implementation breakdown and hands task tracking changes to the host `/specify` workflow.

## It's working if

- Every slice maps to RFC acceptance criteria and has clear dependencies.
- The user approves the breakdown before it is recorded or acted on.
- No duplicate tracker issues or alternative approval state are created.
