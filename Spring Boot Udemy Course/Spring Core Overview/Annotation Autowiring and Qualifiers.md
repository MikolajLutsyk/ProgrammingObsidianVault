# 🔧 Annotation Autowiring & @Qualifier in Spring  
**Tags:** #spring #dependency-injection #autowiring #qualifier #java 

---

## 📌 `@Autowired` ([[Injection Types - which one to use?|Constructor Injection]])

- Tells Spring to **automatically inject** matching beans **by type**
- Recommended: use on **constructors** for required dependencies

```java
@Component
public class OrderService {
    private final PaymentService paymentService;

    @Autowired
    public OrderService(PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

---

## 🎯 `@Qualifier`

- Resolves ambiguity when multiple beans of the **same type** exist
- Use with `@Autowired` to specify **which bean to inject**

```java
@Component
public class OrderService {
    private final PaymentService paymentService;

    @Autowired
    public OrderService(@Qualifier("paypalService") PaymentService paymentService) {
        this.paymentService = paymentService;
    }
}
```

---

## 🧾 Summary

| Annotation   | Purpose                            |
|--------------|-------------------------------------|
| `@Autowired` | Injects bean by type                |
| `@Qualifier` | Selects a specific bean by name     |

> ✅ Always prefer **constructor injection** for required dependencies.
