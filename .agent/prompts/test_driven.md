---
name: Test-Driven Prompt Pattern
description: Enforces Spec-Driven Development by encoding requirements as verifiability tests before any logic is written
---

# Test-Driven Prompt Pattern

## Usage
Use this to enforce Spec-Driven Development. It ensures requirements are encoded as verifiability tests before any logic is written.

## Prompt Template

```
Create JUnit tests for [feature specification] including boundary and failure cases. After tests are written, implement code that passes them.
```

## Example

```
Create JUnit tests for the OrderService.calculateDiscount() method including:
- Boundary cases: 0 items, 1 item, exactly 10 items, 11+ items
- Failure cases: null order, negative quantities, invalid discount codes

After tests are written, implement code that passes them.
```
