---
description: "Ask Codex (gpt-5.2) a question. Use 'medium' or 'xhigh' for different reasoning levels."
argument-hint: "[medium|xhigh] your question"
---

Parse the user's arguments to determine the reasoning level and question.

**Reasoning Levels:**
- `medium` - Faster, simpler responses
- `high` - Default, balanced analysis
- `xhigh` - Deep reasoning, complex analysis

**Usage Examples:**
- `/codex-chat What is the purpose of this function?` → uses high (default)
- `/codex-chat medium Explain this briefly` → uses medium
- `/codex-chat xhigh Design a caching strategy` → uses xhigh

**Execution:**
1. Parse the first word to check if it's a reasoning level (medium, xhigh)
2. If it is, use that level and the rest as the question
3. If not, use "high" as default and treat all args as the question
4. Run: `codex exec -c model_reasoning_effort="<level>" "<question>"`
5. Return the response and note the session ID for potential resumption
