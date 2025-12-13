---
description: "Resume the last Codex conversation or a specific session"
argument-hint: "[session-id]"
---

Resume a previous Codex conversation.

**Usage:**
- `/codex-resume` → Resume the last Codex session
- `/codex-resume 019b18fa-24d4-7e50-a6f2-...` → Resume a specific session

**Execution:**
1. If no argument provided: Run `codex resume --last`
2. If session-id provided: Run `codex resume <session-id>`
3. Continue the conversation from where it left off
