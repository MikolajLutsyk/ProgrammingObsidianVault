# 💤 Lazy Initialization in Spring  
**Tags:** #spring #lazy-initialization #performance #bean-lifecycle #annotations #java 

---

## ⚙️ Default Behavior

- By default, Spring **initializes all beans** at application startup.
- Spring creates an instance of each bean and makes them available immediately.

---

## 🧠 Lazy Initialization

Use `@Lazy` to **defer bean creation** until:

- It is needed for [[Defining Dependency Injection|dependency injection]]
- It is **explicitly requested**

```java
@Lazy
@Component
public class HeavyService { }
```

---

## 🌍 Global Lazy Initialization

Enable lazy initialization **application-wide**:

```properties
spring.main.lazy-initialization=true
```

---

## ✅ Advantages

- 🚀 Faster application startup
- 📦 Only creates objects **on demand**
- 💡 Useful for **large codebases** with many components

---

## ⚠️ Disadvantages

- 🌐 Web components like `@RestController` not created until accessed
- 🧪 Possible late discovery of configuration errors
- 🧠 Must ensure enough memory for all beans when they eventually load

---

> 🧩 Use lazy initialization **selectively** for non-critical or heavy components
