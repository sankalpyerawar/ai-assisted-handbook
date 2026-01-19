---
name: Debugging Pattern
description: Provides context for bug fixing and forces regression test generation
---

# Debugging Pattern

## Usage
Use this when fixing bugs. It provides the AI with the necessary context (environment, stack trace) and forces a regression test to prove the fix.

## Prompt Template

```
Error: [stack trace]. Code snippet: [...]. Task: identify root cause, propose minimal fix, and generate a regression test case.
```

## Example

```
Error:
java.lang.NullPointerException: Cannot invoke "String.length()" because "str" is null
    at com.example.service.StringProcessor.process(StringProcessor.java:42)
    at com.example.controller.ApiController.handleRequest(ApiController.java:28)

Code snippet:
public int process(String str) {
    return str.length();  // Line 42
}

Task:
1. Identify root cause
2. Propose minimal fix
3. Generate a regression test case
```
