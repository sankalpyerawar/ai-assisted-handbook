---
description: Workflow for adding a new feature to an existing codebase
---

# Feature Development (Existing Repo)

When adding a new feature to an existing codebase, follow this loop:

## 1. Context Loading

Read `SPEC.md` and relevant existing code to ensure:
- Full context is loaded
- Architectural drift is prevented

## 2. Architecture Check

Before writing any code, propose:
- Where the new feature fits (package, layer)
- Any necessary data model changes

Get user approval on the placement before proceeding.

## 3. Test-Driven Entry

Create a **failing test stub** (Unit or Integration) that demonstrates:
- The new feature's success cases
- The new feature's failure/edge cases

> [!IMPORTANT]
> Tests must be written BEFORE implementation code.

## 4. Implementation

Write the code required to pass the specific test generated in step 3.

> [!CAUTION]
> Do NOT implement features not covered by tests.

## 5. Review

Verify the output:
- Check against project style guidelines
- Run all tests to ensure no regressions
- Validate architectural consistency
