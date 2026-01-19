# Validation Checklists

Quality gates that must be verified before finalizing any code output.

## Available Checklists

| Checklist | File | When to Use |
|-----------|------|-------------|
| **Master Validation** | `master_validation.md` | Before finalizing ANY code |
| **Security** | `security.md` | Security reviews, all external-facing code |
| **Architecture & Cleanup** | `architecture_cleanup.md` | Refactoring, code cleanup |

---

## Usage

> [!IMPORTANT]
> Before outputting or finalizing any code, run through the relevant checklist. If any item fails, correct the code immediately.

### Automatic Application

- **Master Validation**: Apply to ALL code outputs
- **Security Checklist**: Apply when acting as Security Reviewer
- **Architecture Checklist**: Apply during refactoring/cleanup tasks
