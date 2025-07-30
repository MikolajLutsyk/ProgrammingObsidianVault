# 🔄 Inversion of Control (IoC)  
**Tags:** #spring #ioc #design-principles #java 

---

## 📌 Definition

**Inversion of Control (IoC)** is a design principle where the control of object creation and dependency management is delegated to a container or framework rather than being handled manually in code.

---

## 🌱 In Spring

- Spring IoC container manages beans and their dependencies
- Promotes loose coupling and easier testing
- Achieved through **dependency injection**

---

## 💡 Example

Instead of:
```java
Service service = new ServiceImpl();
```

Spring does:
```java
@Autowired
private Service service;
```

> ✅ IoC allows objects to be wired automatically, reducing hard-coded dependencies.
