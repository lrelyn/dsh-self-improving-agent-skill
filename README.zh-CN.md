# Self-Improving Agent（自我改进型智能体）

一套**工具无关**的 AI 编程助手工作协议：**执行 → 观察 → 反思 → 固化 → 复用**。

适用于任何会读取指令文件的 AI 工具：Claude Code、Codex、Cursor、Gemini CLI、GitHub Copilot、Windsurf、Aider 等。

## 一句话说明

它不会让模型变聪明（权重是固定的），但能让**同一个模型**通过积累记忆、工具和验证，**不再重复踩同样的坑**。

## 零依赖

**不需要任何插件、扩展、npm 包、Python 包或额外软件。**

整套东西就是几个 Markdown 文本文件。你唯一需要的是：一个会读取指令文件的 AI 工具（Claude Code / Codex / Cursor / Gemini CLI / Copilot / Windsurf 等，任选其一你已经在用的），以及一个文本编辑器。

| 项目 | 是否需要 |
|---|---|
| 插件 / 扩展 | ❌ 不需要 |
| npm / pip 包 | ❌ 不需要 |
| 数据库 | ❌ 不需要 |
| 服务器 / Docker | ❌ 不需要 |
| 联网 | ❌ 不需要 |
| 你常用的 AI 工具 | ✅ 需要（你本来就在用） |

## 安装

按你用的工具，把对应入口文件放到**项目根目录**即可：

| 工具 | 入口文件 |
|---|---|
| Codex / 通用 agent | `AGENTS.md` |
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursor/rules/self-improving.mdc` |
| Gemini CLI | `GEMINI.md` |
| Windsurf | `.windsurfrules` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| DSH / 技能体系 | `SKILL.md` |

所有入口都指向同一份协议本体 `AGENTS.md`，内容只维护一份。

### 全局安装（对所有项目生效）

| 工具 | 全局位置 |
|---|---|
| Claude Code | `~/.claude/CLAUDE.md` |
| Codex | `~/.codex/AGENTS.md` |
| Gemini CLI | `~/.gemini/GEMINI.md` |
| Cursor | 设置 → Rules → User Rules（粘贴 `AGENTS.md` 内容） |
| 其他工具 | 把 `AGENTS.md` 内容粘进它的 system / custom instructions |

## 记忆文件

协议把经验存在 `AGENT_MEMORY.md`：

- **项目级**：项目根目录的 `AGENT_MEMORY.md`
- **全局级**：`~/.agent-memory/AGENT_MEMORY.md`

每个作用域只保留一份，不要到处散落副本。`AGENT_MEMORY.md` 默认被 `.gitignore` 排除——它记录的是本机经验，不宜提交到公开仓库。

样例见 [`examples/AGENT_MEMORY.md`](examples/AGENT_MEMORY.md)。

## 它怎么工作

每个真实任务都走这五步：

1. **执行** —— 做任务，记录关键决策和风险假设
2. **观察** —— 回看真实结果：哪里符合预期、哪里偏差、哪步开始出错、花了多少时间/token
3. **反思** —— 按固定格式写一条进 `AGENT_MEMORY.md`
4. **固化** —— 把验证过的解法沉淀成可复用规则/脚本
5. **复用** —— 下次同类任务先查记忆，直接套用已验证的解法

外加一条硬规则：**声称"完成"之前必须自检核验**（输出真的符合要求？关键文件真的存在？边界处理了吗？）。

## 授权

MIT
