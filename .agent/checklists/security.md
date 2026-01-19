# Security Specific Checklist

This checklist focuses strictly on security requirements. AI-generated code is known to have **3x more security flaws** than human code.

> [!CAUTION]
> When acting as the **Security Reviewer**, apply this strict checklist to all code.

---

## Checklist

### 1. Input Validation
- [ ] Is all external input validated using strict constraints?
- [ ] Are JSR 380 annotations used (`@NotNull`, `@Size`, `@Pattern`)?
- [ ] Are validation errors handled gracefully?

### 2. Output Encoding
- [ ] Is data returned to the user escaped to prevent XSS?
- [ ] Are HTML entities encoded properly?
- [ ] Is JSON output sanitized?

### 3. Authentication & Authorization
- [ ] Are access controls enforced at the **service layer**, not just the web layer?
- [ ] Is the principle of least privilege applied?
- [ ] Are sensitive operations protected?

### 4. Dependency Safety
- [ ] Are any new dependencies vetted for licensing?
- [ ] Are dependencies checked for known vulnerabilities (CVEs)?
- [ ] Is the dependency from a trusted source?

### 5. Secret Management
- [ ] Ensure NO keys, tokens, or passwords are present in code
- [ ] Ensure NO secrets are in git history
- [ ] Are secrets externalized to environment variables or secret managers?

---

## OWASP Top 10 Quick Check

| Risk | Question |
|------|----------|
| A01 Broken Access Control | Are permissions checked on every request? |
| A02 Cryptographic Failures | Is sensitive data encrypted in transit and at rest? |
| A03 Injection | Are queries parameterized? |
| A04 Insecure Design | Was security considered in the design phase? |
| A05 Security Misconfiguration | Are defaults secure? |
| A06 Vulnerable Components | Are dependencies up to date? |
| A07 Authentication Failures | Is authentication robust? |
| A08 Data Integrity Failures | Are updates verified? |
| A09 Logging Failures | Are security events logged? |
| A10 SSRF | Are outbound requests validated? |
