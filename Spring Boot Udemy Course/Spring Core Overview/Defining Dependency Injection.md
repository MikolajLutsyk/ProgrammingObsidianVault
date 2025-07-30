# 🧩 Dependency Injection (DI)  
**Tags:** #spring #dependency-injection #ioc #java 

---

## 📌 Definition

**Dependency Injection (DI)** is a design pattern in which an object’s dependencies are provided (injected) by an external system rather than the object creating them itself.

DI is a key part of **[[Inversion of Control]] (IoC)** and is widely used in **Spring Framework** to manage object lifecycles and dependencies.

---

## 🔄 [[Inversion of Control|IoC]] Container in Spring

The **IoC Container** is the core of the Spring Framework.

- Responsible for **creating**, **configuring**, and **managing** beans
- Reads metadata from `@Component`, `@Bean`, `@Configuration`, etc.
- Performs dependency injection automatically

### 🧠 Main Interfaces:
- `ApplicationContext` (commonly used)
- `BeanFactory` (basic version)

Example:
```java
ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
MyService service = context.getBean(MyService.class);
```

---

## 💡 Benefits of DI

- Promotes **loose coupling**
- Enhances **testability**
- Encourages **clean architecture**

---

## 🛠️ Types of Dependency Injection in Spring

| Type            | Example                              |
| --------------- | ------------------------------------ |
| **Constructor** | Preferred method                     |
| **Field**       | Using `@Autowired` on fields         |
| **Setter**      | Using `@Autowired` on setter methods |

---

## ✅ Example (Constructor Injection)

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

> 🧠 Spring automatically resolves and injects dependencies at runtime using the IoC container.
