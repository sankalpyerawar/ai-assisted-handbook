---
name: Skeleton Generation Pattern
description: Creates project boilerplate aligned with Package-by-Feature structure
---

# Skeleton Generation Pattern

## Usage
Use this after the design phase to create boilerplate. It ensures the directory structure aligns with the 'Package-by-Feature' rule.

## Prompt Template

```
Generate a Maven/Gradle project skeleton for a [Java/Kotlin/etc] web service with packages [by feature/domain] and empty classes for each component.
```

## Example

```
Generate a Maven project skeleton for a Java Spring Boot web service with:

Package structure (by feature):
- com.example.order (OrderController, OrderService, OrderRepository, Order entity)
- com.example.user (UserController, UserService, UserRepository, User entity)
- com.example.payment (PaymentController, PaymentService, PaymentRepository)

Include:
- pom.xml with Spring Boot dependencies
- application.yml configuration
- Empty class stubs for each component
- Test directory structure mirroring main
```
