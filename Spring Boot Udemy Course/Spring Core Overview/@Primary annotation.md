# ⭐ @Primary vs [[Annotation Autowiring and Qualifiers|@Qualifier]]  
**Tags:** #spring #dependency-injection #primary #qualifier #autowiring #best-practices #java 

---

## 🟢 `@Primary`

- Marks one bean as the **default implementation**
- Avoids the need to use [[Annotation Autowiring and Qualifiers|qualifiers]]
- ✅ Only **one** bean can be marked as `@Primary`

```java
@Primary
@Component
public class PaypalService implements PaymentService { }
```

---

## ⚠️ Conflicts

- If **multiple beans** are marked as `@Primary`, Spring throws:
  ```
  UnsatisfiedDependencyException
  ```

---

## 🔄 Mixing with [[Annotation Autowiring and Qualifiers|@Qualifier]]

- You can use both together
- `@Qualifier` **overrides** `@Primary` if both are present

```java
@Autowired
public OrderService(@Qualifier("stripeService") PaymentService paymentService) {
    this.paymentService = paymentService;
}
```

---

> ✅ Recommended: Prefer [[Annotation Autowiring and Qualifiers|@Qualifier]] for clarity and precision
