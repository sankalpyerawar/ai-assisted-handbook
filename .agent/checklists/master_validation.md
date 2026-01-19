# Master Validation Checklist (Definition of Done)

This checklist catches defects and vulnerabilities commonly found in AI-generated code.

> [!IMPORTANT]
> **Before outputting or finalizing any code**, verify it against this checklist. If any item fails, correct the code immediately.

---

## Checklist

### 1. Specification Compliance
- [ ] Does the code implement exactly what was asked in `SPEC.md` or the prompt?

### 2. Architecture Fit
- [ ] Is the code in the correct package/layer?
- [ ] Ensure business logic is NOT leaking into controllers or UI layers

### 3. Duplication Check
- [ ] Did you reinvent the wheel?
- [ ] Check if an existing utility or library function already solves this
- [ ] Do NOT duplicate code

### 4. Import Integrity
- [ ] Are all imports real?
- [ ] Verify that NO hallucinated libraries or 'slop squatting' dependencies are included

### 5. Naming & Style
- [ ] Do class names follow `STYLE.md` (e.g., PascalCase for classes)?
- [ ] Do variables follow conventions (e.g., camelCase)?

### 6. Exception Handling
- [ ] Are you using specific, meaningful exceptions?
- [ ] Do NOT catch generic `Exception`
- [ ] Ensure low-level errors are wrapped with context

### 7. Security Sanity
- [ ] **Injection**: Are all SQL queries parameterized?
- [ ] **XSS**: Is output properly encoded/escaped?
- [ ] **Secrets**: Are there ZERO hard-coded credentials?

### 8. Observability
- [ ] Have you added structured logging (SLF4J)?
- [ ] Are metrics added for critical paths?

### 9. Test Coverage
- [ ] Have you generated Unit tests for this feature?
- [ ] Have you generated Integration tests for this feature?

### 10. Documentation
- [ ] Have you updated Javadoc/comments to reflect changes?
