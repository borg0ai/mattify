## What it does

`code-review` checks a diff on two axes: repository standards and fidelity to the originating Approved RFC. The RFC under `.spec/rfc/` defines scope; tickets and PR descriptions can help locate it, but cannot replace it.

It reports standards findings separately from RFC findings, so stylistic concerns cannot hide missing behavior or scope creep.

## When to reach for it

Type `/code-review`, or the agent reaches for it automatically when a review task fits. Reach for it after implementation or when reviewing an existing diff with an Approved RFC. If no RFC is identifiable, route scope clarification through the host-installed `/specify` skill.

## Two independent questions

The **RFC** axis asks whether required behavior is missing, implemented incorrectly, or exceeded. The **standards** axis checks documented repository rules and code quality. Findings on each axis remain distinct.

## Common questions

**Can a tracker ticket replace the RFC?**

No. A ticket can point to the originating RFC, but the review compares the diff with the Approved RFC itself. If it is missing, report that gap rather than skipping the scope review.

## It's working if

- The review identifies the originating Approved RFC and checks its acceptance criteria.
- Standards and RFC findings appear in separate sections.
- Each finding cites concrete changed behavior or a documented standard.
- Scope additions are routed through `/specify`, not accepted from review comments alone.

## Where it fits

`code-review` checks completed implementation before handoff. [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) runs it after building an RFC, while [pr](https://github.com/borg0ai/mattify/blob/main/skills/engineering/pr/SKILL.md) shapes the reviewed change for a pull request. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
