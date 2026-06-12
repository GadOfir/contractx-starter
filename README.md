# CONTRACTX Starter

**Self-growing AI agent contracts.** Drop this in your repo, ask your agent to interview you, and never argue about "I assumed X" again.

## Quick start

```bash
git clone https://github.com/GadOfir/contractx-starter.git
cd your-project
# Copy these files in:
cp -r ../contractx-starter/CONTRACTX.md .
cp -r ../contractx-starter/CONTRACTX .
cp -r ../contractx-starter/.claude/skills/contractx .claude/skills/
```

Then tell your AI agent:

> **"Interview me for CONTRACTX init."**

The agent reads `prompts/interview.md`, asks you deep architectural questions about your project, and builds the entire CONTRACTX tree. 20 minutes. One time.

## What you get

| File/Folder | Purpose |
|---|---|
| `CONTRACTX.md` | Root framework rail — rules, protocol, child index |
| `CONTRACTX/` | Artifacts — gaps, audits, cross-cutting contracts, refs |
| `.claude/skills/contractx/SKILL.md` | The contractx skill — init, walk, update, audit, gap, grow |
| `prompts/interview.md` | The deep interview prompt — give this to your agent once |

## How it works

1. **Walk before edit** — agent reads root → parent → child CONTRACTX.md chain before touching any file
2. **Update after edit** — agent updates nearest CONTRACTX.md after meaningful changes
3. **Gap tracking** — CX-NNN gaps in `CONTRACTX/gaps/`, never deleted
4. **Audit** — `/contractx audit` walks every CONTRACTX.md, checks for drift

## No dependencies

Just markdown files and a skill. Works with Claude Code, Codex, OpenCode, Cursor, or any agent that reads instruction files.
