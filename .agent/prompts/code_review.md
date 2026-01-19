---
name: Code Review Pattern
description: Triggers the Reviewer role to produce structured reports without rewriting code
---

# Code Review Pattern

## Usage
Use this to trigger the 'Reviewer' role. It forces the AI to produce a structured report rather than rewriting the code, preventing it from introducing new bugs while trying to 'fix' style issues.

## Prompt Template

```
Perform a structured code review on the following change. Checklist: identify security or performance risks, highlight anti-patterns, and suggest improvements with minimal edits. Output inline comments, a risk summary, and an improvement checklist.
```

## Example

```
Perform a structured code review on the following change.

Checklist:
- Identify security or performance risks
- Highlight anti-patterns
- Suggest improvements with minimal edits

Output:
- Inline comments referencing specific lines
- Risk summary
- Improvement checklist

[paste diff or code here]
```
