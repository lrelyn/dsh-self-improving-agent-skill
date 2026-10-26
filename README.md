# Self-Improving Agent

English | [简体中文](README.zh-CN.md)

This repository provides a tool-agnostic self-improving protocol for AI coding agents.

**Zero dependencies** — no plugins, npm/pip packages, database, server, or Docker. It is just Markdown files plus an AI tool you already use. See [Requirements](#requirements).

**Read and follow [AGENTS.md](AGENTS.md).**

## Requirements

**Nothing beyond a text file and an AI tool.**

| Item | Needed? |
|---|---|
| Plugins / extensions | ❌ No |
| npm / pip packages | ❌ No |
| Database | ❌ No |
| Server / Docker | ❌ No |
| Network access | ❌ No |
| An AI coding tool (Claude Code / Codex / Cursor / Gemini CLI / Copilot / Windsurf / …) | ✅ Yes — whichever you already use |
| A text editor | ✅ Yes |

This is a pure-instruction repository: Markdown files that the agent reads. There is no code to build or run.

## Install

Pick the entry file for your tool — all of them point to the same protocol:

| Tool | Entry file | Where to put it |
|---|---|---|
| Claude Code | `CLAUDE.md` | project root |
| Codex / generic agents | `AGENTS.md` | project root |
| Cursor | `.cursor/rules/self-improving.mdc` | project root |
| Gemini CLI | `GEMINI.md` | project root |
| Windsurf | `.windsurfrules` | project root |
| GitHub Copilot | `.github/copilot-instructions.md` | project root |
| Any other agent | paste `AGENTS.md` into its system/custom instructions | — |

For a **global** install (applies to every project):

- Claude Code: `~/.claude/CLAUDE.md`
- Codex: `~/.codex/AGENTS.md`
- Cursor: Settings → Rules → User Rules
- Gemini CLI: `~/.gemini/GEMINI.md`

## Memory

The protocol stores lessons in `AGENT_MEMORY.md`:

- project scope → `AGENT_MEMORY.md` in the project root
- global scope → `~/.agent-memory/AGENT_MEMORY.md`

Keep one memory file per scope. `AGENT_MEMORY.md` is git-ignored by default — it holds machine-local lessons.

## What it does

Applies **Act → Observe → Reflect → Codify → Reuse** to every real task, plus a mandatory self-verification checklist before claiming work is done. It does not make a model smarter; it makes the same model stop repeating mistakes by accumulating memory, tools, and verification.

## License

MIT
