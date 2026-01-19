---
name: Refactoring + Safety Pattern
description: Prevents breaking existing functionality when cleaning up code by demanding a diff
---

# Refactoring + Safety Pattern

## Usage
Use this when cleaning up code. It explicitly prevents the AI from breaking existing functionality or overwriting unrelated logic by demanding a diff.

## Prompt Template

```
Refactor this function for readability/performance. Rules: preserve all behavior and side effects. Do not modify logging or API responses. Output a unified diff only.
```

## Example

```
Refactor the following OrderProcessor.processOrder() method for readability and performance.

Rules:
- Preserve all behavior and side effects
- Do not modify logging statements
- Do not change API responses
- Output a unified diff only

[paste code here]
```
