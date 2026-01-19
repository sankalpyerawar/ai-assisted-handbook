# Java-Specific Rules (Enterprise/Spring Boot)

These rules apply specifically to Java development, with focus on enterprise patterns and Spring Boot applications.

---

## 7. Architecture & Package Structure

Follow Clean/Hexagonal Architecture. Keep business logic pure and independent of outer frameworks (web/database). Organize code by feature (Package-by-Feature) where services, controllers, and repositories for a domain live together, rather than by technical layer.

---

## 8. Dependency Injection Standards

Use Spring Dependency Injection (DI) everywhere. Mandatory dependencies must use constructor injection to ensure immutability and prevent null states. Do not use the `new` keyword for system classes or framework components; let the container manage them.

---

## 9. Immutability & Typing

Favor immutable objects. Use Java `record` classes for DTOs and entity IDs to auto-generate final fields. Prefer explicit types (e.g., `List<String>`) over `var` in public APIs and complex logic to maintain readability.

**Strict Typing Requirements:**
- No raw types allowed (e.g., use `List<String>` not `List`)
- Mandatory JavaDoc for all public APIs
- Check for existing dependencies in `pom.xml`/`build.gradle` before importing new ones

---

## 10. Exception Handling

Use checked exceptions for recoverable conditions and runtime exceptions for programming errors. Do not throw generic `Exception`. Define custom exceptions (e.g., `OrderNotFoundException`) and wrap lower-level exceptions with meaningful messages to preserve context.

---

## 11. Testing Standards (Java)

Use JUnit 5 for testing. Mirror the production package structure in `src/test/java`. Use Mockito to isolate classes under test. Ensure tests cover one feature per method and verify edge cases. Use `@SpringBootTest` for integration tests.

---

## 12. Logging & Observability

Use SLF4J with a structured format (JSON). Distinct log levels (ERROR, WARN, INFO, DEBUG) appropriately. Do not concatenate strings in logs; use parameterization (e.g., `log.info("User {}", userId)`). Never log sensitive data like passwords.

---

## 13. Input Validation

Rigorously validate all external inputs using Jakarta Bean Validation (JSR 380) annotations (e.g., `@NotNull`, `@Size`) on DTOs. Validate early to prevent bad data from bubbling up. Throw meaningful exceptions for invalid inputs.
