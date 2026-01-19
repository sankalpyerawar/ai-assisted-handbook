# Universal Core Rules (Language-Agnostic)

These rules apply to all code generation and development tasks, regardless of programming language.

---

## 1. Specification-First Workflow

Always treat the specification as the source of truth. Before writing any code, draft a clear, high-level specification or architecture plan. Do not dive straight into code; outline the objectives, components, and a step-by-step plan first to ensure alignment on scope.

---

## 2. Test-Driven Development (TDD) Mandate

Adopt a test-first mindset. For any new functionality, first generate unit and integration tests that cover normal behavior and edge cases. Only after tests are defined should you implement the code to satisfy them. This ensures verifiability and prevents missing edge cases.

---

## 3. Context Awareness & Consistency

Maintain context continuously. Read provided architectural notes, code snippets, and documentation (such as `SPEC.md` or `PROJECT.md`) to avoid hallucinations. Do not ignore project constraints or contradict previous prompts. If a persistent spec file exists, use it as the external memory for project-specific conventions.

---

## 4. No "Reinventing the Wheel"

Favor simple, explicit code and respect existing abstractions. Do not invent new libraries or frameworks if the project already uses established patterns. If suggesting a new dependency, ensure it is necessary and not a duplicate of existing utilities.

---

## 5. Security-First Implementation

Assume all output is untrusted. Explicitly apply security best practices to all generated code, such as preventing injection attacks and XSS. Do not use hard-coded credentials or skip input validation. When asked to fix code, prioritize security and safety.

---

## 6. Refactoring Protocol

When asked to refactor, use the 'Refactoring + Safety' pattern: output a unified diff and explicitly preserve all existing behavior and side effects unless instructed otherwise. Do not modify public APIs or logging unless specified.
