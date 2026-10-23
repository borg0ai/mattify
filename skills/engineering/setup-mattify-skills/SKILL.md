---
name: setup-mattify-skills
description: "Prepare a repository for Mattify's RFC-first workflow. Use when starting with Mattify or when the repository has no valid .spec/ setup."
disable-model-invocation: true
---

# Setup Mattify Skills

Prepare the current repository to create and track RFCs with the host-installed `specify` skill. This skill does not create a second RFC implementation.

## Process

1. Confirm the current working directory is the repository the user wants to configure.
2. Check whether `.spec/ROADMAP.md`, `.spec/TASK_TRACKING.md`, and `.spec/rfc/` exist. If they do, ask the host `specify` skill to run `sync-check`; do not overwrite existing RFCs.
3. If `.spec/` is absent, call the Skill tool with `specify` and ask it to initialize this repository. Let that skill scaffold the RFC files.
4. Confirm the host skill reports success and the `.spec/` files exist. If the skill is unavailable or fails, report its exact result and stop. Do not create the files by hand or fall back to an issue tracker.
5. Explain that new product, behavior, and architecture work starts with an RFC, and implementation waits for explicit RFC approval.

## Boundaries

- Mattify does not bundle the `specify` skill. The user's agent environment must provide it.
- `.spec/` is the RFC authority. Do not create parallel specs, decision tickets, or issue-tracker workflows.
- Do not change Git remotes, publish, or push as part of setup.
