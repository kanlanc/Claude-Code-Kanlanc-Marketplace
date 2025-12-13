# codex-consulting

Consult OpenAI Codex (gpt-5.2) for second opinions, code analysis, and expert insights.

## Prerequisites

- [Codex CLI](https://github.com/openai/codex) installed: `npm install -g @openai/codex`
- Valid OpenAI/ChatGPT subscription with Codex access

## Installation

```bash
claude plugins add kanlanc/Claude-Code-Kanlanc-Marketplace/codex-consulting
```

## Commands

| Command | Description |
|---------|-------------|
| `/codex-chat [medium\|xhigh] <question>` | Ask Codex a question (default: high reasoning) |
| `/codex-resume [session-id]` | Resume last Codex conversation |
| `/codex-review` | Get Codex to review staged git changes |

### Examples

```bash
# Ask a question with default (high) reasoning
/codex-chat What's the best way to handle authentication in this codebase?

# Ask with medium reasoning (faster)
/codex-chat medium Explain this function

# Ask with extra-high reasoning (deeper analysis)
/codex-chat xhigh Design a caching strategy for this API

# Resume last conversation
/codex-resume

# Resume specific session
/codex-resume 019b18fa-24d4-7e50-a6f2-...

# Review staged changes
/codex-review
```

## Skills

Skills are auto-invoked by Claude when your request matches their triggers.

| Skill | Trigger Phrases | Reasoning | Purpose |
|-------|-----------------|-----------|---------|
| codex-chat | "ask codex", "codex opinion" | high | General consultation |
| codex-thinkdeep | "codex deep analysis", "investigate with codex" | xhigh | Multi-step investigation |
| codex-debug | "codex debug", "codex root cause" | xhigh | Root cause analysis |
| codex-codereview | "codex review code" | high | Code review |
| codex-consensus | "codex perspectives", "pros and cons" | high | Multi-perspective analysis |
| codex-resume | "continue codex", "resume codex" | - | Resume last session |

### Skill Examples

```
# Auto-invokes codex-thinkdeep skill
"Use codex to do a deep analysis of the authentication flow"

# Auto-invokes codex-debug skill
"Ask codex to debug this timeout issue"

# Auto-invokes codex-consensus skill
"Get codex perspectives on whether we should use Redux or Context"
```

## Session Resumption

Codex maintains conversation sessions automatically:

```bash
# Each exec creates a session
codex exec "analyze this code"
# Output shows: session id: 019b18fa-24d4-7e50-a6f2-...

# Resume the last session
/codex-resume

# Or resume a specific session
/codex-resume 019b18fa-24d4-7e50-a6f2-...
```

## Agent

The `codex-agent` can be spawned as a background agent for longer consultations:

```
Use the codex-agent to analyze the security implications of our current auth implementation
```

## Reasoning Levels

| Level | Flag | Use Case |
|-------|------|----------|
| medium | `-c model_reasoning_effort="medium"` | Quick answers, simple queries |
| high | (default) | Most consultations |
| xhigh | `-c model_reasoning_effort="xhigh"` | Deep analysis, complex debugging |
