# ai-council

Multi-model AI council for ensemble consulting with Codex (GPT-5.2) and Gemini. Query both models in parallel and get synthesized responses.

## Prerequisites

- [Codex CLI](https://github.com/openai/codex) installed: `npm install -g @openai/codex`
- [Gemini CLI](https://github.com/google-gemini/gemini-cli) installed
- Valid API subscriptions for both services

## Installation

```bash
claude plugins add kanlanc/Claude-Code-Kanlanc-Marketplace/ai-council
```

## Commands

| Command | Description |
|---------|-------------|
| `/council-chat [medium\|xhigh] <question>` | Ask both Codex and Gemini, get synthesized response |
| `/council-resume [codex\|gemini]` | Resume last session for specified model |
| `/council-review` | Review staged git changes with both models |

### Examples

```bash
# Ask the council a question (default: high reasoning)
/council-chat What's the best architecture for this feature?

# Ask with extra-high reasoning for deep analysis
/council-chat xhigh Analyze the security implications of this auth flow

# Review staged changes
/council-review

# Resume last Codex conversation
/council-resume codex
```

## Skills

Skills are auto-invoked by Claude when your request matches their triggers.

| Skill | Trigger Phrases | Purpose |
|-------|-----------------|---------|
| council-chat | "ask council", "council opinion", "what do the AIs think" | General consultation |
| council-thinkdeep | "council deep analysis", "investigate with council" | Multi-step investigation |
| council-debug | "council debug", "council root cause" | Root cause analysis |
| council-codereview | "council review code" | Code review |
| council-consensus | "council perspectives", "council pros and cons" | Multi-perspective analysis |

### Skill Examples

```
# Auto-invokes council-thinkdeep skill
"Use the council for a deep analysis of the authentication flow"

# Auto-invokes council-debug skill
"Ask the council to debug this timeout issue"

# Auto-invokes council-consensus skill
"Get council perspectives on whether we should use Redux or Context"
```

## Response Format

The council provides synthesized responses in this format:

```markdown
## AI Council Response

### Codex (GPT-5.2) Says:
[Codex's analysis]

### Gemini Says:
[Gemini's analysis]

### Council Synthesis:
**Agreement:** Points both models agree on
**Divergence:** Where they differ
**Recommendation:** Synthesized recommendation

---
*Session IDs: Codex=[id], Gemini=[id]*
```

## Safety

Both models run in read-only sandbox mode:
- Codex: `--sandbox read-only`
- Gemini: `-s -y`

This ensures no destructive commands can execute.

## Agent

The `council-agent` can be spawned as a background agent for longer consultations:

```
Use the council-agent to analyze the architecture of our microservices
```
