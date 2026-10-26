# Self-Improving Agent

A tool-agnostic working protocol for AI coding agents: **Act → Observe → Reflect → Codify → Reuse**.

Works with any agent that reads instruction files: Claude Code, Codex, Cursor, Gemini CLI, GitHub Copilot, Windsurf, Aider, and others.

## The memory file

This protocol keeps its long-term memory in one plain-text file:

```
AGENT_MEMORY.md
```

**Location rule (portable, no absolute paths):**

- Prefer a repo/project-local `AGENT_MEMORY.md` next to this file.
- For cross-project memory, use `~/.agent-memory/AGENT_MEMORY.md`.
- If neither exists, create one at the location that matches the scope you are working in.
- Never hard-code machine-specific absolute paths into committed content.

Keep exactly **one** memory file per scope. Do not scatter copies.

## Protocol (apply to every real task)

1. **Before** — skim `AGENT_MEMORY.md` for prior lessons matching this task. Reuse verified solutions instead of rediscovering failures.
2. **During** — note key decisions: tools/commands used, and which assumptions might be wrong.
3. **After** — append one entry to the memory file (even a single line), using the structure below. Never write to a stray copy.
4. **Judge objectively** — where a result can be checked mechanically (exit code, file exists, HTTP 200, data complete, test passes), use that. Do not rely on a subjective "looks done".

## Memory entry format

```
### <date> <task in one line>
- Worked: <what went right>
- Failed: <what broke and why>
- Next time: <concrete change, specific steps over vague intent>
- Reusable: <can it become a command / rule / prompt snippet?>
```

## Working loop

### 1. Act
Do the task. Record key decision points and risky assumptions.

### 2. Observe
Review the actual result: did output match expectation, where did it diverge, where did it start failing, what did it cost (time/tokens).

### 3. Reflect
Write the entry into `AGENT_MEMORY.md` with the format above.

### 4. Codify
Turn verified, repeatable solutions into durable assets:
- multi-step flows used repeatedly → save as a reusable rule/skill/script
- single commands or tricks → record under "Reusable" in the memory file
- long histories → use the agent's own context-compaction/search tools

### 5. Reuse
Next time a similar task appears, check `AGENT_MEMORY.md` and existing rules first, then apply the verified approach.

## Mandatory self-verification

Before claiming anything is "done", verify:

1. The output actually meets the requirement — not merely resembles it.
2. Key data/files really exist and contain what is claimed.
3. Obvious gaps and unhandled edge cases are addressed.

## Principles

- Capability does not increase by itself — weights are fixed. Improvement comes from accumulating **memory + tools + verification**.
- Write at least one entry per significant task.
- Prefer few and specific over many and vague.
- Never commit secrets, credentials, or machine-local paths into public content; keep `.env`, keys, and private memory out of version control.
