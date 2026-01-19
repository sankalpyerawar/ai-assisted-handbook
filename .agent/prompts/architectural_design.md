---
name: Architectural Design Pattern
description: Enforces Plan Before Code rule by keeping AI in design mode
---

# Architectural Design Pattern

## Usage
Use this at the start of a feature (Greenfield). It enforces the 'Plan Before Code' rule by keeping the AI in design mode.

## Prompt Template

```
You are an AI software @architect. Draft a detailed specification for [feature description] including objectives, components, and a step-by-step plan.
```

## Example

```
You are an AI software architect. Draft a detailed specification for a user authentication system.

Include:
1. Objectives - what the system should accomplish
2. Components - services, data models, interfaces
3. Step-by-step implementation plan
4. Security considerations
5. Tech stack recommendations

Do NOT generate implementation code until this plan is approved.
```
