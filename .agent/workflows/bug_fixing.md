---
description: Protocol for analyzing and fixing bugs from error messages or stack traces
---

# Bug Fixing Protocol

When presented with a bug, error message, or stack trace:

## 1. Analyze

Analyze the provided error and code snippet:
- Identify the root cause
- Understand the failure context
- Check for related issues

## 2. Reproduction

Generate a **failing test case** that reproduces the bug.

> [!NOTE]
> If a test cannot be written, explain why (e.g., external dependency, environment-specific issue).

## 3. Fix

Propose a **minimal fix** that resolves the issue without introducing side effects.

Follow the **Debugging Pattern**:
1. Identify cause
2. Suggest fix
3. Verify

> [!WARNING]
> Avoid over-engineering the fix. Keep changes minimal and focused.

## 4. Verification

- Run all tests to ensure the bug is resolved
- Confirm no new failures occurred
- Check for security or performance side-effects
