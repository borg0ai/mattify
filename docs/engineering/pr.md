## What it does

`pr` gives a pull request body three parts: a compact view of the change, concrete evidence, and a statement of merge risk. It is a writing aid, not permission to expand approved scope.

The Summary names the originating Approved RFC. That link lets reviewers compare the proposed merge with the decision that authorized the work.

## When to reach for it

Type `/pr`, or the agent reaches for it automatically when writing a PR body. Reach for it after implementation and review, when the body should explain an RFC-scoped change. If the originating RFC is unclear or not Approved, settle it through the host-installed `/specify` skill before presenting the PR as ready.

## Evidence over claims

The **evidence** section reports what actually ran or was observed. A screenshot can show a visual result; command output or checks can show other behavior. Do not claim tests passed if they were not run.

## Common questions

**What belongs in the Summary?**

The RFC ID and path, plus the smallest diagram or diff view that explains the shipped change. Keep it tied to approved scope.

## It's working if

- Summary names the originating Approved RFC.
- A reviewer can understand the change before opening the diff.
- Evidence names observed results without inventing verification.
- Merge risk reflects the actual blast radius and reversibility.

## Where it fits

`pr` prepares the handoff after [code-review](https://github.com/borg0ai/mattify/blob/main/skills/engineering/code-review/SKILL.md) has checked implementation against its RFC. [implement](https://github.com/borg0ai/mattify/blob/main/skills/engineering/implement/SKILL.md) produces the change; [ask-matt](https://github.com/borg0ai/mattify/blob/main/skills/engineering/ask-matt/SKILL.md) routes across Mattify's skills.
