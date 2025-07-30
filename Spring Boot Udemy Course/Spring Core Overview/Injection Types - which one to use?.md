# 💉 Dependency Injection: Constructor vs Setter  
**Tags:** #spring #dependency-injection #best-practices #java 

---

## 🏗️ Constructor Injection

- ✅ Use when you have **required dependencies**
- 🥇 **Recommended** by the Spring team as the **first choice**
- Promotes **immutability** and helps with **unit testing**
- Makes dependencies **explicit** and avoids partially constructed objects

```java
@Component
public class MyService {
    private final UserRepository userRepository;

    @Autowired
    public MyService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }
}
```

---

## 🛠️ [[Setter Injection]]

- 🔄 Use when you have **optional dependencies**
- App can provide **default logic** if dependency is missing
- May allow more **flexibility**, but less clear about what's required

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

> 🧠 Use **constructor injection** by default, and fall back to **[[setter injection]]** only when dependencies are optional.
