---
name: to-tickets
description: "Break an Approved RFC into implementation slices and acceptance checks without creating a competing scope or approval source."
disable-model-invocation: true
---

# To Tickets

Use this skill only after the host-installed `/specify` skill has created and the user has approved an RFC. The Approved RFC remains the authority for scope and decisions.

1. Read the complete Approved RFC and relevant repository context.
2. Propose the smallest independently verifiable implementation slices, ordered by dependency. Keep each slice within the RFC's scope and acceptance criteria.
3. Ask the user to approve the breakdown before recording or acting on it.
4. Hand the approved breakdown to the host-installed `specify` skill for any `.spec/TASK_TRACKING.md` changes. Never edit RFC lifecycle files directly or publish duplicate tracker tickets.

If no Approved RFC exists, stop and use host-installed `/specify` to create and approve one first. A task breakdown does not authorize implementation; use `implement` or `implement-spec` only after the RFC is Approved.
