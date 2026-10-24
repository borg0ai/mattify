## What it does

`to-spec` is a compatibility command that hands confirmed project decisions to the host-installed `/specify` skill. It does not create or edit RFC files, publish tracker issues, or approve work.

## When to reach for it

You invoke this by typing `/to-spec`; the agent won't reach for it on its own. Use it when a settled software product, behavior, or architecture change needs an RFC. For direct RFC lifecycle work, use the host-installed `/specify` skill.

## Where it fits

This is an RFC handoff step. Mattify's interview and research skills can prepare inputs, while `/specify` owns RFC files, validation, status, and approval. Use [implement](../../skills/engineering/implement/SKILL.md) after the RFC is Approved. The [ask-matt](../../skills/engineering/ask-matt/SKILL.md) router maps the full skill set.

## Common questions

**Does Mattify include `/specify`?**

No. Install the host's `specify` skill separately. This command stops if that skill is unavailable.

**Can `/to-spec` approve or publish the RFC?**

No. It passes the confirmed context to `/specify`, then waits for that workflow and the user's explicit approval.

## It's working if

- Host `/specify` receives a concise summary of confirmed decisions and open questions.
- No RFC or issue tracker files are written by `/to-spec` itself.
- Implementation waits for an Approved RFC.
