---
description: "Get both Codex and Gemini to review staged git changes"
---

# Council Review Command

Have both Codex and Gemini review your staged git changes in parallel.

## Usage

```
/council-review
```

## Execution

1. Get staged git changes:
   ```bash
   git diff --staged
   ```

2. Run **BOTH** reviews in parallel:

   **Codex:**
   ```bash
   codex exec --sandbox read-only -a never -c model_reasoning_effort="high" "Review these git changes for bugs, security issues, and improvements:\n\n<diff>"
   ```

   **Gemini:**
   ```bash
   gemini -s -y -o json "Review these git changes for bugs, security issues, and improvements:\n\n<diff>"
   ```

3. Synthesize findings from both models

## Response Format

```markdown
## AI Council Code Review

### Codex (GPT-5.2) Review:
**Issues Found:**
- [List of issues]

**Suggestions:**
- [List of suggestions]

---

### Gemini Review:
**Issues Found:**
- [List of issues]

**Suggestions:**
- [List of suggestions]

---

### Council Synthesis:
**Critical Issues (Both Agree):**
- [Issues identified by both models]

**Additional Concerns:**
- [Issues only one model caught]

**Recommended Actions:**
1. [Prioritized action items]

---
*Session IDs: Codex=[id], Gemini=[id]*
```

## Notes

- Requires staged changes (`git add` first)
- Both models run in read-only sandbox mode
- Review focuses on: bugs, security, performance, style
