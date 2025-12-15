---
description: "Ask both Codex (gpt-5.2) and Gemini a question. Use 'medium' or 'xhigh' for different reasoning levels."
---

# Council Chat Command

Query both Codex and Gemini in parallel, then synthesize their responses.

## Usage

```
/council-chat [medium|xhigh] <question>
```

## Reasoning Levels

- **medium**: Quick answers, simple queries
- **high**: Default for most consultations
- **xhigh**: Deep analysis, complex problems

## Execution

1. Parse the user's question and reasoning level
2. Run **BOTH** commands in parallel:

   **Codex:**
   ```bash
   codex exec --sandbox read-only -c model_reasoning_effort="<level>" "<question>"
   ```

   **Gemini:**
   ```bash
   gemini -s -y -o json "<question>"
   ```

3. Collect both responses
4. Synthesize and present the combined response

## Response Format

```markdown
## AI Council Response

### Codex (GPT-5.2) Says:
[Codex response]

### Gemini Says:
[Gemini response]

### Council Synthesis:
**Agreement:** [Points both models agree on]
**Divergence:** [Where they differ]
**Recommendation:** [Synthesized recommendation]

---
*Session IDs: Codex=[id], Gemini=[id]*
*Use `/council-resume codex` or `/council-resume gemini` to continue*
```

## Examples

```
/council-chat What's the best way to handle authentication?
/council-chat xhigh Design a caching strategy for this API
/council-chat medium Explain this function briefly
```
