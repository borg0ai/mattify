---
name: domain-modeling
description: Build and sharpen a project's domain model. Use when discussing codebase terminology or writing or editing a GLOSSARY.md; route software product, architecture, and behavior proposals through /specify RFCs.
---

# Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the *active* discipline: challenging terms, inventing edge-case scenarios, and writing resolved vocabulary down as it crystallises. Proposed product, architecture, and behavior decisions go through `/specify` as an RFC; a separate implementation ADR can follow RFC approval when it meets the bar below. (Merely *reading* `GLOSSARY.md` for vocabulary is not this skill: that's a one-line habit any skill can do. This skill is for when you're changing the model, not just consuming it.)

## File structure

Most repos have a single context:

```
/
├── GLOSSARY.md
├── docs/
│   └── adr/
│       ├── 0001-event-sourced-orders.md
│       └── 0002-postgres-for-write-model.md
└── src/
```

If a `GLOSSARY-MAP.md` exists at the root, the repo has multiple contexts. The map points to where each one lives:

```
/
├── GLOSSARY-MAP.md
├── docs/
│   └── adr/                          ← system-wide decisions
├── src/
│   ├── ordering/
│   │   ├── GLOSSARY.md
│   │   └── docs/adr/                 ← context-specific decisions
│   └── billing/
│       ├── GLOSSARY.md
│       └── docs/adr/
```

Create files lazily: only when you have something to write. If no `GLOSSARY.md` exists, create one when the first term is resolved. Do not create an ADR to record a proposed product, architecture, or behavior change; route that proposal through `/specify` and its RFC. Existing ADRs remain useful context. After an RFC is approved, an ADR may record a separate durable implementation decision when the project uses ADRs.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in `GLOSSARY.md`, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y. Which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account': do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible. Which is right?"

### Update GLOSSARY.md inline

When a term is resolved, update `GLOSSARY.md` right there. Don't batch these up: capture them as they happen. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

`GLOSSARY.md` should be totally devoid of implementation details. Do not treat `GLOSSARY.md` as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Keep proposal and implementation records separate

Use the host-installed `/specify` skill to create an RFC for proposed product, architecture, or behavior changes. Do not create issue specs or ADRs as substitutes. Once an RFC is approved, an ADR can document a distinct implementation trade-off if all three conditions hold: it is hard to reverse, surprising without context, and resulted from a real choice among alternatives. Use [ADR-FORMAT.md](./ADR-FORMAT.md) for that post-approval record.
