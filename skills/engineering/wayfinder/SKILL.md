---
name: wayfinder
description: Help shape a large, uncertain effort into an RFC hierarchy through the host-installed /specify skill. Use when scope spans multiple decisions or sessions and needs an umbrella RFC with child RFCs.
disable-model-invocation: true
---

# Wayfinder

Wayfinder helps clarify a large effort whose destination is known but whose decisions are not settled. Its output is decision input for the host-installed `/specify` skill, which owns RFC creation, status, and task tracking.

## Boundary

- Do not create a parallel map, decision tickets, or implementation tickets on an issue tracker.
- Do not create, edit, approve, or advance RFC files directly. Use the host-installed `/specify` skill for the RFC lifecycle and its CLI for managed files.
- Keep implementation scope in Approved RFCs under `.spec/rfc/`. Do not begin product implementation while decisions remain unresolved or the relevant RFC is not Approved.
- An issue, PR, or conversation may supply evidence and context. It does not become the scope artifact.

## Chart the effort

1. State the destination in one or two sentences. Determine what the completed RFC set must let a team decide or build.
2. Explore the whole effort breadth-first. List known decisions, evidence needed, dependencies, and uncertain areas. Keep facts separate from assumptions and open questions.
3. Split only concerns that can be decided and reviewed independently. Recommend one umbrella RFC and child RFCs when the effort has multiple concerns; recommend one RFC when it does not.
4. Present the decision map and dependencies in the conversation. Do not write a tracker map or tickets.
5. Hand the settled direction to the host-installed `/specify` skill to create or update the RFC hierarchy. Follow its validation and approval workflow.

## Continue an RFC effort

1. Read the umbrella RFC and relevant child RFCs from `.spec/`.
2. Select one unresolved decision or research question. Do not claim that an unapproved child RFC authorizes implementation.
3. Investigate local code or authoritative external sources as appropriate. Present evidence and options for the user to decide.
4. Send decisions or scope changes through `/specify`. Do not write the RFC files or task tracking yourself.
5. Stop after one decision handoff. Resume with the updated RFC state in a later session.

If the route is already clear and the effort fits one session, skip wayfinding and ask `/specify` to create the RFC directly. If an Approved RFC already defines the work, use `implement` or `implement-spec` instead.
