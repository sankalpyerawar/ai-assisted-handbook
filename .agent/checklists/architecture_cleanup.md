# Architecture & Cleanup Checklist

This checklist prevents **architecture drift** and **code sprawl**.

> [!IMPORTANT]
> When performing **Refactoring** or **Cleanup**, verify all items below.

---

## Checklist

### 1. Immutability
- [ ] Are DTOs immutable (e.g., Java `record` classes)?
- [ ] Are value objects immutable?
- [ ] Are collections returned as unmodifiable copies?

### 2. Dependency Injection Patterns
- [ ] Is **Constructor Injection** used for all mandatory dependencies?
- [ ] Is there NO field injection (`@Autowired` on fields)?
- [ ] Are optional dependencies handled via setter injection or `Optional`?

### 3. Clean Boundaries
- [ ] Does the code strictly adhere to **Clean Architecture**?
- [ ] Inner layers do NOT depend on outer layers
- [ ] Domain logic is framework-independent

```
┌─────────────────────────────────────┐
│         Frameworks & Drivers        │  ← Outer (Web, DB, UI)
├─────────────────────────────────────┤
│        Interface Adapters           │  ← Controllers, Gateways
├─────────────────────────────────────┤
│         Application Layer           │  ← Use Cases
├─────────────────────────────────────┤
│          Domain / Entities          │  ← Inner (Pure Business Logic)
└─────────────────────────────────────┘
          Dependencies point INWARD →
```

### 4. No Silent Failures
- [ ] Are exceptions logged with stack traces at the **ERROR** level before being handled?
- [ ] Are failures visible in monitoring/alerting?
- [ ] Is there no swallowing of exceptions without logging?

---

## Quick Verification

```java
// ✅ GOOD: Constructor injection, immutable
@Service
public class OrderService {
    private final OrderRepository repository;
    
    public OrderService(OrderRepository repository) {
        this.repository = repository;
    }
}

// ❌ BAD: Field injection, mutable
@Service
public class OrderService {
    @Autowired
    private OrderRepository repository;
}
```
