# Saved Prompts & Patterns

This directory contains reusable prompt patterns for common development tasks.

## Available Patterns

| Pattern | File | Purpose |
|---------|------|---------|
| Test-Driven | `test_driven.md` | TDD enforcement |
| Refactoring + Safety | `refactoring_safety.md` | Safe code cleanup |
| Code Review | `code_review.md` | Structured review reports |
| Debugging | `debugging.md` | Root cause analysis |
| Explainer | `explainer.md` | Documentation & onboarding |
| Architectural Design | `architectural_design.md` | Plan before code |
| Skeleton Generation | `skeleton_generation.md` | Project boilerplate |

---

## Usage Guidelines

### ✅ DO

- Use structured patterns that define **input**, **task**, and **output format**
- Verify AI suggestions with tests (especially for debugging fixes)
- Refine context or specification if a pattern doesn't work

### ❌ DON'T (Anti-Patterns)

| Anti-Pattern | Problem | Solution |
|--------------|---------|----------|
| **Open-Ended Wording** | "What's the best way to do X?" leads to vague responses | Use structured patterns with clear inputs/outputs |
| **Prompt Thrashing** | Asking the same thing repeatedly | If it fails twice, stop and refine the context |
| **Blind Trust** | Accepting fixes without verification | Always verify with regression tests |

---

## Quick Reference

```
# TDD Pattern
Create JUnit tests for [feature] including boundary and failure cases.
After tests are written, implement code that passes them.

# Refactoring Pattern
Refactor for readability/performance. Preserve behavior. Output diff only.

# Code Review Pattern
Perform structured review. Output: inline comments, risks, improvements.

# Debugging Pattern
Error: [trace]. Code: [...]. Task: root cause, minimal fix, regression test.

# Explainer Pattern
Explain step-by-step, tracing data flow. Provide annotated comments.

# Architecture Pattern
Draft specification: objectives, components, step-by-step plan.

# Skeleton Pattern
Generate Maven/Gradle skeleton with package-by-feature structure.
```
