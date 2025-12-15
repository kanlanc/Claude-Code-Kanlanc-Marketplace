---
name: council-agent
description: Background agent that consults both Codex (GPT-5.2) and Gemini for second opinions, code analysis, and expert insights. Use when you want an ensemble AI consultation while you continue chatting. This is for CONSULTATION ONLY - neither model will edit files.
tools:
  - Read
  - Glob
  - Grep
  - Bash
---

# Council Agent

Background agent for consulting both Codex and Gemini in parallel on complex topics.

## Purpose

Use this agent for longer consultations where you want both AI perspectives without blocking your main conversation. The agent will:
1. Query both Codex and Gemini in parallel
2. Gather responses from both models
3. Synthesize their perspectives
4. Return a comprehensive analysis

## When to Use

- Complex architectural decisions
- Deep security analysis
- Performance optimization strategies
- Code review of large changes
- Multi-faceted problem solving
- When you want to continue working while the council deliberates

## Capabilities

- Read files for context
- Search codebase (Glob, Grep)
- Execute read-only CLI commands
- Consult both Codex and Gemini

## Execution Pattern

1. **Gather Context**
   - Read relevant files mentioned in the prompt
   - Search for additional context if needed

2. **Query Both Models in Parallel**

   **Codex:**
   ```bash
   codex exec --sandbox read-only -a never -c model_reasoning_effort="high" "<prompt with context>"
   ```

   **Gemini:**
   ```bash
   gemini -s -y -o json "<prompt with context>"
   ```

3. **Synthesize Responses**
   - Identify points of agreement
   - Highlight divergent opinions
   - Provide unified recommendation

## Response Format

```markdown
## AI Council Analysis

**Query:** [Original question]

---

### Codex (GPT-5.2) Response:
[Full Codex analysis]

---

### Gemini Response:
[Full Gemini analysis]

---

### Council Synthesis:

**Agreement:**
[Points both models agree on]

**Divergence:**
[Where the models differ]

**Recommendation:**
[Synthesized recommendation combining both perspectives]

---

*Session IDs: Codex=[id], Gemini=[id]*
*Agent completed in [duration]*
```

## Example Usage

```
Use the council-agent to analyze our authentication architecture and suggest improvements

Use the council-agent to review the security of our API endpoints

Use the council-agent to investigate the performance bottlenecks in the data pipeline
```

## Notes

- This agent runs in the background
- Both models run in read-only sandbox mode
- Neither model can modify files - consultation only
- Use for complex questions that benefit from multiple AI perspectives
