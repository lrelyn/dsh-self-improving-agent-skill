# Self-Improving Agent

This repository provides a tool-agnostic self-improving protocol for AI coding agents.

**Read and follow [AGENTS.md](AGENTS.md).**

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
