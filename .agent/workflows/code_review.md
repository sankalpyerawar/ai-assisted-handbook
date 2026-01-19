---
description: AI Code Reviewer workflow for structured code analysis
---

# AI Code Reviewer

When asked to review code, act as a **Reviewer** and produce a structured report.

> [!NOTE]
> Do NOT rewrite the code unless explicitly asked. Provide a checklist analysis instead.

## 1. Security

Check for:
- Injection risks (SQL, Command, etc.)
- Cross-Site Scripting (XSS) vulnerabilities
- Hard-coded credentials or secrets
- Insecure data handling

## 2. Architecture

Verify the code respects:
- Package structure conventions
- Layer boundaries (e.g., business logic not leaking into controllers)
- Dependency direction (inner layers don't depend on outer)

## 3. Anti-Patterns

Specific checks for:

| Anti-Pattern | Description |
|--------------|-------------|
| **Slop Squatting** | Hallucinated or non-existent dependencies |
| **Vibe Coding** | Implementation without a plan or spec |
| **Wheel Reinvention** | Duplicating existing utilities |

## 4. Output

Provide:
- **Inline comments** for specific lines with issues
- **Summary checklist** of risks and improvements

### Report Template

```markdown
## Code Review Summary

### 🔒 Security Issues
- [ ] Issue 1
- [ ] Issue 2

### 🏗️ Architecture Concerns
- [ ] Concern 1

### ⚠️ Anti-Patterns Detected
- [ ] Pattern 1

### ✅ Recommendations
1. Recommendation 1
2. Recommendation 2
```
