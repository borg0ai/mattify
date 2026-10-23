## What it does

`grill-with-docs` interviews you about a plan or design until you and the [agent](https://www.aihero.dev/ai-coding-dictionary/agent) share one understanding of it, and writes resolved vocabulary into your repo while it does. It is the same interview [grill-me](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grill-me/SKILL.md) runs (a round of questions, then wait, then the next round), pointed at a codebase.

It is **[stateful](https://www.aihero.dev/ai-coding-dictionary/stateful)**. Every other grilling skill leaves the [session](https://www.aihero.dev/ai-coding-dictionary/session) in your head; this one leaves domain vocabulary on disk. When a term resolves, the skill writes it to `GLOSSARY.md` at once, not in a batch at the end. For a software product, architecture, or behavior change, the confirmed decisions go to the host-installed `/specify` skill, which records the proposal as an RFC. An ADR is not a substitute for that RFC.

## When to reach for it

You invoke this by typing `/grill-with-docs`, and the agent won't reach for it on its own.

Reach for it at the start of a change, in a repo, when the plan is still fuzzy and the words for the thing are not settled yet. It is the single-session tool. Which grilling skill you want depends on what is in front of you:

| What you have | Reach for |
| --- | --- |
| You aren't working in a working directory at all | [grill-me](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grill-me/SKILL.md) |
| A repo, and a change you can settle in one session | `grill-with-docs` |
| An effort too big to hold in one session (a greenfield build, a large feature) | [wayfinder](https://github.com/borg0ai/mattify/blob/main/skills/engineering/wayfinder/SKILL.md) |
| A repo with no domain docs at all, and no particular feature in mind | `grill-with-docs`, aimed at the repo rather than a change |
| A decision blocked on knowledge in someone else's head | [to-questionnaire](https://github.com/borg0ai/mattify/blob/main/skills/productivity/to-questionnaire/SKILL.md) |

The wayfinder split comes down to session count: `/grill-with-docs` for single-session planning, `/wayfinder` for multi-session planning.

## Prerequisites

The skill writes resolved terms into a `GLOSSARY.md` at the root, or into the relevant context's glossary when a root `GLOSSARY-MAP.md` marks the repo as multi-context. You need permission to write there. RFC creation is a separate handoff to the host-installed `/specify` skill after you confirm the shared understanding.

It also needs two other skills present, because its own `SKILL.md` is one line that delegates to them. [grilling](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grilling/SKILL.md) supplies the interview, and [domain-modeling](https://github.com/borg0ai/mattify/blob/main/skills/engineering/domain-modeling/SKILL.md) supplies the writing. Installing `grill-with-docs` alone gets you a skill that does not work.

## The paper trail

Three things come out of a session, and they are not equal.

| What resolved | Where it lands |
| --- | --- |
| A term: the project's own word for a thing | `GLOSSARY.md`, inline, the moment it resolves |
| A software product, architecture, or behavior proposal | The host-installed `/specify` skill creates an RFC from this conversation |
| A separate implementation trade-off after RFC approval | An ADR, only when the project uses ADRs and the choice merits one |
| An unrelated discussion | The conversation, without a forced RFC |

`GLOSSARY.md` is only a glossary. It holds no implementation details, no [spec](https://www.aihero.dev/ai-coding-dictionary/spec), and no scratch notes. The confirmed design decisions remain in the conversation until `/specify` turns a software change into an RFC. Do not publish issue specs or create an ADR in place of that RFC.

The glossary is the main output. This skill builds domain language: the project's own words, agreed once, so you, the agent and your colleagues do not have to work them out again. Not everyone agrees that this improves agent performance. The strongest objection is that a term and its plain-English expansion get the same result from the [model](https://www.aihero.dev/ai-coding-dictionary/model), and that the vocabulary mainly shortens communication between the humans who share it. On that view the glossary is still valuable, but the value goes to the humans.

## Common questions

**Should I use this or `/wayfinder`?**
Scope decides it. Use this for anything you can settle in one session; use [wayfinder](https://github.com/borg0ai/mattify/blob/main/skills/engineering/wayfinder/SKILL.md) when the effort is too big to hold in one, and it charts the work as a map of decision [tickets](https://www.aihero.dev/ai-coding-dictionary/ticket) first. Wayfinder is slower and denser, and reaching for it on a well-scoped feature is the common mistake. It does not replace this skill, and it can start a grilling session for the parts of the map that suit one.

**It ran, but no `GLOSSARY.md` or RFC appeared.**
No glossary change is expected if no term was resolved. RFC creation is a separate step: after you confirm shared understanding for a software change, hand the same conversation to the host-installed `/specify` skill. If that handoff was requested but no RFC was created, check the skill's result before proceeding.

**It asked everything at once, with no recommendations, and never mentioned `GLOSSARY.md`.**
That is the skill failing to load its two dependencies. Because `SKILL.md` is a one-line delegation, an agent that does not pick up [grilling](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grilling/SKILL.md) and [domain-modeling](https://github.com/borg0ai/mattify/blob/main/skills/engineering/domain-modeling/SKILL.md) guesses at what grilling means, and you get every question at once with no structure. Partial loading is more confusing. `grilling` loads, `domain-modeling` does not, and you get a good interview with no paper trail. How often it happens depends on the model and the [effort](https://www.aihero.dev/ai-coding-dictionary/effort) level, and it is the most reported problem with this skill. If you suspect it, ask the agent directly which skills it loaded.

**Where did all my other decisions go?**
They stay in the conversation until you confirm the understanding. For software product, architecture, or behavior changes, invoke the host-installed `/specify` skill in that same conversation to create the RFC, then check that it preserves the settled requirements and constraints. An ADR or issue spec is not a replacement.

**Can I point it at an existing repo that has no docs at all?**
Yes. This is the right skill for a codebase with no ADRs, no domain language and no design principles: invoke it and say "help me document my repo". Users often pair it with [improve-codebase-architecture](https://github.com/borg0ai/mattify/blob/main/skills/engineering/improve-codebase-architecture/SKILL.md) for building or repairing a `GLOSSARY.md`. Expect to steer it. It reads code and asks you about what it finds, and you decide which of the words already in the codebase are the right ones.

**What should I do when the session ends?**
Confirm the shared understanding. For a software product, architecture, or behavior change, continue in the same conversation with the host-installed `/specify` skill and create an RFC before implementation. Unrelated discussions can end with the shared understanding.

**Why is it called that?**
Nobody is happy with the name. There is an open suggestion to rename it `grill-domain-model`, which describes the behaviour more accurately. Nothing has moved on it. If a rename ever lands, the docs page moves with it and the URL changes.

## It's working if

- `GLOSSARY.md` changes *during* the session, term by term, rather than appearing in one lump at the end.
- The glossary reads as pure vocabulary (your project's words with tight definitions) and contains no implementation detail or spec-like prose.
- Questions the codebase can answer get answered by reading the codebase, not asked of you.
- Product, architecture, and behavior proposals land in an RFC through `/specify`; no ADR or issue spec stands in for it.
- It challenges a word you used because your existing glossary defines it differently.

## Where it fits

`grill-with-docs` establishes shared understanding for a software change, then hands it to `/specify`:

```txt
grill-with-docs → /specify → approved RFC → implementation
```

It produces the shared understanding and settled vocabulary that `/specify` uses to create an RFC without interviewing you again. Its close neighbours are [grill-me](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grill-me/SKILL.md), the same interview with no repo and no files, and [domain-modeling](https://github.com/borg0ai/mattify/blob/main/skills/engineering/domain-modeling/SKILL.md), the glossary discipline it drives; both use the [grilling](https://github.com/borg0ai/mattify/blob/main/skills/productivity/grilling/SKILL.md) primitive. For unrelated discussions, the conversation itself can be the endpoint. When unsure which skill or flow fits, [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes you.
