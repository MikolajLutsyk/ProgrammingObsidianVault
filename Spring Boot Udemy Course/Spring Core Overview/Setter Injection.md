# 🛠️ Setter Injection in Spring  
**Tags:** #spring #dependency-injection #setter-injection #java 

---

## 📌 Definition

**Setter Injection** is a form of [[Defining Dependency Injection|dependency injection]] where Spring injects dependencies by calling **setter methods** on your class after the object is constructed.

---

## 📦 When to Use

- ✅ Use when the dependency is **optional**
- 🔄 Allows setting or changing dependencies **after object creation**
- 💡 Provides flexibility and supports **default logic** if no dependency is provided

---

## 💡 Example

```java
@Component
public class MyService {
    private EmailService emailService;

    @Autowired
    public void setEmailService(EmailService emailService) {
        this.emailService = emailService;
    }
}
```

> 🔧 Spring calls the setter automatically and injects the appropriate bean.

---

## ⚠️ Considerations

- Less explicit than constructor injection
- Can allow partially initialized objects
- Use only when **optional configuration** or **late injection** is needed

---

> 🧠 Preferred approach: **Constructor Injection** for required dependencies, **Setter Injection** for optional ones.
