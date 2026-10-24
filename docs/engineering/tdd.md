## What it does

`tdd` guides a red-green loop: one failing test, the smallest implementation that passes, then the next behavior. For product work, an Approved RFC supplies expected behavior and agreed test seams.

The RFC is the independent source of truth. If it does not define the behavior or seam well enough to test, stop and settle it through the host-installed `/specify` skill instead of inventing requirements in a test.

## When to reach for it

Type `/tdd`, or the agent reaches for it automatically when a task fits. Reach for it when implementing an Approved RFC behavior through a stable public interface. For an undecided behavior, use `/specify`; for implementing a full RFC, use [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md).

## The loop and the seam

The **seam** is the public boundary where a test observes behavior without depending on internals. An RFC that names the expected behavior and seam makes each red-green cycle small and reviewable. No test should silently expand the RFC's scope.

Mocks belong at external boundaries. Expected values come from the RFC or another independent source, not from the implementation being tested.

## Common questions

**What if the RFC does not name a test seam?**

Do not guess where acceptance should be observed. Present the candidate seams and their tradeoffs, then use `/specify` to record the decision before writing tests.

## It's working if

- Each test checks behavior named by the Approved RFC.
- The test runs red for the expected reason before implementation.
- Tests observe public behavior, not private calls or internal state.
- A missing requirement sends the work back to `/specify`.

## Where it fits

`tdd` guides the implementation step; it does not create or approve RFCs. [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) and [implement-spec](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement-spec/SKILL.md) can use its loop, while [code-review](https://github.com/borg0ai/mattify/blob/main/skills/engineering/code-review/SKILL.md) checks the result against the RFC. [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
