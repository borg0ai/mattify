## What it does

`setup-mattify-skills` prepares a repository to use Mattify's RFC-first workflow. It checks for `.spec/` and routes initialization or consistency checks to the host-installed `specify` skill.

Mattify does not ship a second RFC engine. The `specify` skill owns the RFC files, status changes, and cross-file checks.

## When to reach for it

You invoke this by typing `/setup-mattify-skills`; the agent won't reach for it on its own. Run it when onboarding a repository or when its `.spec/` setup is missing or inconsistent. For creating or advancing an RFC directly, use the host's `/specify` skill.

## Common questions

**Does Mattify include `/specify`?**

No. Install `specify` in your agent environment. Mattify uses that skill as the RFC lifecycle authority.

**Will setup overwrite existing RFCs?**

No. Existing `.spec/` files are checked with `sync-check`. Setup stops on a failure and reports it.

## It's working if

- `.spec/ROADMAP.md`, `.spec/TASK_TRACKING.md`, and `.spec/rfc/` exist.
- The host `specify` skill reports `sync-check` success.
- New implementation work waits for an explicitly approved RFC.

## Where it fits

`setup-mattify-skills` is a run-once onboarding helper. The host `/specify` skill creates and manages RFCs; [ask-matt](../../skills/engineering/ask-matt/SKILL.md) routes supporting research, decisions, and implementation work.
