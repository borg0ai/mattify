---
name: to-spec
description: "Compatibility entry point for turning settled project decisions into an RFC through the host-installed /specify skill."
disable-model-invocation: true
---

# To Spec

This compatibility skill does not create, edit, approve, or publish RFC files. The host-installed `specify` skill owns the RFC lifecycle and `.spec/` consistency.

When invoked for a product, behavior, or architecture change:

1. Summarize the confirmed problem, decisions, evidence, constraints, and open questions from the current conversation.
2. Call the Skill tool with `specify` and pass that summary as input to create or update the RFC.
3. Do not implement the change. Wait for the host `/specify` workflow to validate the RFC and obtain explicit approval.

If the host `specify` skill is unavailable, explain that dependency and stop. Do not fall back to publishing an issue-tracker spec or writing `.spec/` files directly.
