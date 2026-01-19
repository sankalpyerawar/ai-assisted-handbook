---
description: Safe refactoring workflow with strict behavior preservation
---

# Refactoring & Cleanup

When asked to refactor code, strict adherence to the **Refactoring + Safety** pattern is required:

## 1. Pre-Check

Ensure unit tests exist for the code being refactored.

> [!IMPORTANT]
> If tests do not exist, **generate them first** to cover current behavior before making any changes.

## 2. Refactor

Output a **unified diff only**.

Strictly preserve all existing:
- Behavior
- Side effects
- Logging
- API responses

...unless explicitly instructed to change them.

## 3. Constraints

> [!CAUTION]
> Do NOT modify public APIs or remove logging unless specified.

Focus refactoring on:
- **Readability** improvements
- **Performance** optimizations
- **Structure** enhancements

## 4. Review

Verify that the refactored code passes the original tests.

Run the full test suite to confirm no regressions.
