[![Mattify Skills](https://res.cloudinary.com/total-typescript/image/upload/v1777382277/skill-repo-light_2x.png)](https://github.com/borg0ai/mattify)

# Mattify Skills

English | [简体中文](./README.zh-CN.md)

[![skills.sh](https://skills.sh/b/borg0ai/mattify)](https://skills.sh/borg0ai/mattify)

Mattify is a community-maintained fork of [Matt Pocock's agent skills](https://github.com/mattpocock/skills). It keeps the skills' practical engineering techniques and reshapes their workflow around RFCs created and managed by the host-installed `/specify` skill.

Mattify does not bundle or replace `/specify`. Use `/specify` to create, validate, review, and approve RFCs. Mattify skills help gather evidence and decisions for an RFC, then implement work only from an Approved RFC. Install the host's `specify` skill separately.

This fork retains upstream attribution to Matt Pocock. Workflow changes and maintenance belong to the Mattify project.

## Installation

A plugin updates itself. [skills.sh](https://skills.sh/b/borg0ai/mattify) copies editable files into your project, and you update them by hand. Pick one per agent, because installing both gives you every skill twice.

### 1. Get the skills

#### Claude Code

```bash
claude plugin install mattify-skills@claude-plugins-official
```

Updates itself by default.

#### Codex

```bash
codex plugin marketplace add borg0ai/mattify
codex plugin add mattify-skills@mattify
```

Updates itself at startup.

#### GitHub Copilot (CLI and VS Code)

```bash
copilot plugin marketplace add borg0ai/mattify
copilot plugin install mattify-skills@mattify
```

Then, once, add to `~/.copilot/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "mattify": { "source": { "source": "github", "repo": "borg0ai/mattify" }, "autoUpdate": true }
  }
}
```

In VS Code, run **Chat: Install Plugin From Source** and enter `https://github.com/borg0ai/mattify`. It updates daily.

#### Gemini CLI (manual updates)

```bash
gemini skills install https://github.com/borg0ai/mattify.git --path skills/engineering
gemini skills install https://github.com/borg0ai/mattify.git --path skills/productivity
```

Re-run both commands to update.

#### Any other agent, or editable files (manual updates)

```bash
npx skills@latest add borg0ai/mattify -a <agent>  # cursor, opencode, devin, windsurf, amp, pi; omit -a to choose
```

When the installer asks which skills to take, include `setup-mattify-skills`. To update, run `npx skills@latest update`, and re-run `add` to pick up new skills.

### 2. Set up `/specify`

Install the host-provided `specify` skill in your agent environment. Use `/setup-mattify-skills` to check a repository's `.spec/` setup. Then use `/specify` to create and advance RFCs.

## Why Mattify Forks the Skills

Matt Pocock's skills provide useful engineering practices: clarify decisions, research uncertain questions, prototype, test, and review. Their original workflow also relies on tracker-published specs and tickets. Mattify keeps the practices and changes the workflow because project decisions need one durable, reviewable source of truth.

Mattify uses RFCs for product, behavior, and architecture changes. The host-installed `/specify` skill owns RFC creation, validation, status, and approval. Mattify does not bundle a competing RFC tool or use tracker labels and tickets as approval signals.

The workflow is:

1. Use Mattify skills to clarify the problem and gather evidence.
2. Use host-installed `/specify` to create and validate an RFC.
3. Implement only after the RFC is Approved.

## Reference

Skills are grouped by who can invoke them. **User-invoked** skills run only when you type them (e.g. `/grill-me`) and orchestrate a workflow. **Model-invoked** skills can run when the task fits and hold reusable practices. A user-invoked skill may invoke model-invoked skills, but never another user-invoked one.

### Engineering

Engineering workflows and practices.

**User-invoked**

- **[ask-matt](./skills/engineering/ask-matt/SKILL.md)**: Ask which skill or flow fits your situation. A router over the user-invoked skills in this repo.
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)**: Grilling session that also builds your project's domain model, sharpening terminology and updating `GLOSSARY.md` and ADRs inline.
- **[triage](./skills/engineering/triage/SKILL.md)**: Move issues through a state machine of triage roles.
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)**: Scan a codebase for deepening opportunities, present them as a visual HTML report, then grill through whichever one you pick.
- **[setup-mattify-skills](./skills/engineering/setup-mattify-skills/SKILL.md)**: Check a repository's `.spec/` setup and route initialization or consistency checks to host-installed `/specify`.
- **[to-spec](./skills/engineering/to-spec/SKILL.md)**: Compatibility entry point that delegates RFC creation and lifecycle to host-installed `/specify`.
- **[to-tickets](./skills/engineering/to-tickets/SKILL.md)**: Break an Approved RFC into implementation slices while keeping the RFC as scope authority.
- **[implement](./skills/engineering/implement/SKILL.md)**: Implement work from an Approved RFC, using `/tdd` at agreed seams and `/code-review` before completion.
- **[implement-spec](./skills/engineering/implement-spec/SKILL.md)**: Implement an Approved RFC across an integration branch, tracking task dependencies and closing with `/code-review`.
- **[wayfinder](./skills/engineering/wayfinder/SKILL.md)**: Clarify large, uncertain efforts and hand settled decisions to host-installed `/specify` for an RFC hierarchy.
- **[retro](./skills/engineering/retro/SKILL.md)**: Suggest improvements to the coding agent's environment (navigation, automated checks, coding standards, steering files, tooling) after a session, most severe first.

**Model-invoked**

- **[prototype](./skills/engineering/prototype/SKILL.md)**: Build a throwaway prototype to answer a design question, either a single shareable file for state or logic questions, or several radically different UI variations toggleable from one route.
- **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)**: Disciplined diagnosis loop for hard bugs and performance regressions: build a feedback loop that goes red on this bug → minimise → hypothesise → instrument → fix → regression-test.
- **[research](./skills/engineering/research/SKILL.md)**: Investigate a question against high-trust primary sources and capture the findings as a cited Markdown file in the repo, run as a background agent.
- **[tdd](./skills/engineering/tdd/SKILL.md)**: Test-driven development with a red-green-refactor loop. Builds features or fixes bugs one vertical slice at a time.
- **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)**: Actively build and sharpen a project's domain model: challenge terms against the glossary, stress-test with edge-case scenarios, and update `GLOSSARY.md` and ADRs inline.
- **[codebase-design](./skills/engineering/codebase-design/SKILL.md)**: Shared discipline and vocabulary for designing deep modules: a lot of behaviour behind a small interface, placed at a clean seam, testable through that interface.
- **[code-review](./skills/engineering/code-review/SKILL.md)**: Two-axis review of the diff since a fixed point: **Standards** (does it follow the repo's coding standards, plus a Fowler smell baseline?) and **Spec** (does it faithfully implement the originating issue/spec?), run as parallel sub-agents so neither pollutes the other.
- **[pr](./skills/engineering/pr/SKILL.md)**: The shape a pull request body should take: a summary as the smallest visual that makes the change clear, before/after evidence that it works, and a merge-danger call (one-way or two-way door, plus blast radius).
- **[wizard](./skills/engineering/wizard/SKILL.md)**: Generate an interactive bash wizard that walks a human through steps only they can perform: provisioning infrastructure, setting up credentials or CI secrets, walking an unfamiliar third-party dashboard, or running a one-off migration or cutover.

### Productivity

General workflow tools, not code-specific.

**User-invoked**

- **[grill-me](./skills/productivity/grill-me/SKILL.md)**: Get relentlessly interviewed about a plan or design until every branch of the design tree is resolved.
- **[handoff](./skills/productivity/handoff/SKILL.md)**: Compact the current conversation into a handoff document so another agent can continue the work.
- **[teach](./skills/productivity/teach/SKILL.md)**: Teach the user a new skill or concept over multiple sessions, using the current directory as a stateful teaching workspace.
- **[to-questionnaire](./skills/productivity/to-questionnaire/SKILL.md)**: Turn a decision you can't answer alone into a Markdown questionnaire for the one person who can, filled in async, or together over a meeting. It grills you about the send (who it's for, what you need back), not the subject.
- **[wait-what](./skills/productivity/wait-what/SKILL.md)**: Fire this the moment a message doesn't land. The agent re-pitches it with the context you're missing, in plain English, using your `GLOSSARY.md` vocabulary.

**Model-invoked**

- **[grilling](./skills/productivity/grilling/SKILL.md)**: Interview the user about a plan, decision, or idea until key branches are resolved; feed confirmed project decisions into `/specify` when an RFC is needed.
- **[writing-for-agents](./skills/productivity/writing-for-agents/SKILL.md)**: Writing documents for agents: skills, AGENTS.md/CLAUDE.md, and any doc an agent reaches by a pointer.
