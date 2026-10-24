# Mattify Skills

[English](./README.md) | 简体中文

[![skills.sh](https://skills.sh/b/borg0ai/mattify)](https://skills.sh/b/borg0ai/mattify)

Mattify 是 [Matt Pocock agent skills](https://github.com/mattpocock/skills) 的社区维护 fork。项目保留实用的软件工程方法，并将工作流调整为通过宿主环境安装的 `/specify` 创建和管理 RFC。

Mattify 不打包，也不替代 `/specify`。使用 `/specify` 创建、校验、审查并批准 RFC。Mattify 技能负责澄清决策、收集证据，并仅根据已批准的 RFC 实施变更。请在 agent 环境中单独安装宿主提供的 `specify` 技能。

本项目保留对 Matt Pocock 的上游致谢；RFC 优先的流程改造和后续维护由 Mattify 负责。

## 安装

插件会自行更新。[skills.sh](https://skills.sh/b/borg0ai/mattify) 会把可编辑文件复制到项目中，需要手动更新。每种 agent 选择一种安装方式，同时安装两种会导致技能重复。

### 1. 安装技能

#### Claude Code

```bash
claude plugin install mattify-skills@claude-plugins-official
```

默认自动更新。

#### Codex

```bash
codex plugin marketplace add borg0ai/mattify
codex plugin add mattify-skills@mattify
```

默认在启动时自动更新。

#### GitHub Copilot（CLI 和 VS Code）

```bash
copilot plugin marketplace add borg0ai/mattify
copilot plugin install mattify-skills@mattify
```

然后在 `~/.copilot/settings.json` 中添加一次：

```json
{
  "extraKnownMarketplaces": {
    "mattify": { "source": { "source": "github", "repo": "borg0ai/mattify" }, "autoUpdate": true }
  }
}
```

在 VS Code 中运行 **Chat: Install Plugin From Source**，输入 `https://github.com/borg0ai/mattify`。插件每天自动更新。

#### Gemini CLI（手动更新）

```bash
gemini skills install https://github.com/borg0ai/mattify.git --path skills/engineering
gemini skills install https://github.com/borg0ai/mattify.git --path skills/productivity
```

更新时重新运行这两条命令。

#### 其他 agent 或可编辑文件（手动更新）

```bash
npx skills@latest add borg0ai/mattify -a <agent>  # cursor、opencode、devin、windsurf、amp、pi；省略 -a 可选择 agent
```

安装器询问要安装哪些技能时，选择 `setup-mattify-skills`。更新已安装技能时运行 `npx skills@latest update`；安装新增技能时重新运行 `add`。

### 2. 配置 `/specify`

在 agent 环境中安装宿主提供的 `specify` 技能。运行 `/setup-mattify-skills` 检查仓库的 `.spec/` 配置，然后用 `/specify` 创建和推进 RFC。

## 为什么 fork 并改造工作流

Matt Pocock 的技能提供了实用的软件工程方法，例如澄清需求、研究不确定问题、制作原型、测试和审查。上游工作流也依赖发布到 issue tracker 的 spec 和 tickets。Mattify 保留这些工程方法，并改用 RFC 作为单一、持久且可审查的决策依据。

涉及产品、行为或架构变更时，RFC 是唯一的范围和批准来源。宿主 `/specify` 负责 RFC 创建、校验、状态和批准。Mattify 不提供第二套 RFC 工具，也不把 tracker 标签或 ticket 状态当作批准信号。

工作流：

1. 使用 Mattify 技能澄清问题并收集证据。
2. 使用宿主 `/specify` 创建并校验 RFC。
3. RFC 获批后再开始实施。

## 技能索引

技能按调用方式分组。**用户调用**技能只有在你输入命令时才会运行，负责组织工作流。**模型调用**技能也可由 agent 根据任务自动调用，提供可复用的方法。用户调用技能可以调用模型调用技能，但不能调用另一个用户调用技能。

### Engineering

面向软件工程的工作流与方法。

**用户调用**

- **[ask-matt](./skills/engineering/ask-matt/SKILL.md)**：根据目标选择合适的 Mattify 技能和工作流。
- **[grill-with-docs](./skills/engineering/grill-with-docs/SKILL.md)**：通过访谈澄清软件变更，同时维护项目术语表和架构决策记录。
- **[triage](./skills/engineering/triage/SKILL.md)**：分析新收到的问题和外部 PR；产品变更必须进入 `/specify` RFC 流程。
- **[improve-codebase-architecture](./skills/engineering/improve-codebase-architecture/SKILL.md)**：扫描代码库中的模块改进机会，生成可视化报告并深入分析所选机会。
- **[setup-mattify-skills](./skills/engineering/setup-mattify-skills/SKILL.md)**：检查仓库的 `.spec/` 配置，并将初始化和一致性检查交给宿主 `/specify`。
- **[to-spec](./skills/engineering/to-spec/SKILL.md)**：兼容入口，将 RFC 创建和生命周期管理交给宿主 `/specify`。
- **[to-tickets](./skills/engineering/to-tickets/SKILL.md)**：将已批准 RFC 拆分为实现切片，不建立并行的范围或批准来源。
- **[implement](./skills/engineering/implement/SKILL.md)**：根据已批准 RFC 实施一个变更，配合 `/tdd` 和 `/code-review`。
- **[implement-spec](./skills/engineering/implement-spec/SKILL.md)**：根据已批准的父子 RFC 协调多部分变更，并完成代码审查。
- **[wayfinder](./skills/engineering/wayfinder/SKILL.md)**：澄清大型、决策尚未收敛的工作，并交给宿主 `/specify` 建立 RFC 层级。
- **[retro](./skills/engineering/retro/SKILL.md)**：回顾编码过程，提出 agent 环境改进建议。

**模型调用**

- **[prototype](./skills/engineering/prototype/SKILL.md)**：制作一次性原型，回答状态、逻辑或界面设计问题。
- **[diagnosing-bugs](./skills/engineering/diagnosing-bugs/SKILL.md)**：按步骤复现、定位并修复疑难 bug 和性能回退。
- **[research](./skills/engineering/research/SKILL.md)**：基于可信的一手来源开展研究，并将引用证据记录为 Markdown。
- **[tdd](./skills/engineering/tdd/SKILL.md)**：使用 red-green-refactor 循环，以小步方式实现功能或修复问题。
- **[domain-modeling](./skills/engineering/domain-modeling/SKILL.md)**：澄清领域术语和边界场景，维护术语表与架构决策记录。
- **[codebase-design](./skills/engineering/codebase-design/SKILL.md)**：提供深模块设计词汇和方法，帮助定义小接口、清晰边界与可测试 seam。
- **[code-review](./skills/engineering/code-review/SKILL.md)**：从代码规范和已批准 RFC 两个维度审查变更。
- **[pr](./skills/engineering/pr/SKILL.md)**：撰写清楚说明变更、验证证据和合并风险的 PR 描述。
- **[wizard](./skills/engineering/wizard/SKILL.md)**：生成交互式向导，处理必须由人完成的配置、凭据或迁移步骤。

### Productivity

通用工作流工具，不限于软件开发。

**用户调用**

- **[grill-me](./skills/productivity/grill-me/SKILL.md)**：围绕计划或设计持续提问，直到关键决策收敛。
- **[handoff](./skills/productivity/handoff/SKILL.md)**：把当前对话整理成可供其他 agent 接手的交接文档。
- **[teach](./skills/productivity/teach/SKILL.md)**：在当前工作区持续讲解新技能或概念。
- **[to-questionnaire](./skills/productivity/to-questionnaire/SKILL.md)**：把需要他人回答的问题整理成问卷，支持异步填写或共同讨论。
- **[wait-what](./skills/productivity/wait-what/SKILL.md)**：当信息没有讲清楚时，用更直白的语言重新解释。

**模型调用**

- **[grilling](./skills/productivity/grilling/SKILL.md)**：访谈用户，厘清计划、决策或想法；软件变更的确认结果可交给 `/specify` 创建 RFC。
- **[writing-for-agents](./skills/productivity/writing-for-agents/SKILL.md)**：编写 agent 技能、AGENTS.md、CLAUDE.md 和其他 agent 文档。
