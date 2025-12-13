---
description: "Get Codex to review staged git changes"
---

Review staged git changes with Codex.

**Execution:**
1. Get staged changes: `git diff --staged`
2. If no staged changes, inform the user
3. Create a review prompt with the diff
4. Run: `codex exec "Review this code for bugs, security issues, and improvements: <diff>"`
5. Return Codex's code review with actionable feedback

**Review focuses on:**
- Potential bugs or logic errors
- Security vulnerabilities
- Code quality and best practices
- Performance considerations
- Suggestions for improvement
