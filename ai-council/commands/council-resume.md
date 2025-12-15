---
description: "Resume the last Codex or Gemini conversation session"
---

# Council Resume Command

Resume a previous conversation session with either Codex or Gemini.

## Usage

```
/council-resume [codex|gemini] [session-id]
```

## Parameters

- **model**: Which model to resume (`codex` or `gemini`)
- **session-id**: Optional specific session ID (defaults to latest)

## Execution

**For Codex:**
```bash
# Resume latest session
codex --resume

# Resume specific session
codex --resume <session-id>
```

**For Gemini:**
```bash
# Resume latest session
gemini --resume latest

# Resume specific session by index
gemini --resume <index>
```

## List Available Sessions

**Codex:** Sessions are managed automatically
**Gemini:** `gemini --list-sessions`

## Response Format

```markdown
## Resumed Session

**Model:** [Codex or Gemini]
**Session:** [id or latest]

[Continued conversation...]
```

## Examples

```
/council-resume codex
/council-resume gemini
/council-resume codex 019b18fa-24d4-7e50-a6f2-...
/council-resume gemini 5
```
