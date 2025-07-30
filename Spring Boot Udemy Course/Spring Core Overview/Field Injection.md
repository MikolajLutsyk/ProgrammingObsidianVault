# 📥 Field Injection in Spring  
**Tags:** #spring #dependency-injection #field-injection #java 

---

## 📌 What is Field Injection?

**Field Injection** is a form of [[Defining Dependency Injection|dependency injection]] where Spring injects dependencies **directly into fields**, including `private` ones, using **[[Java Reflection]]**.

---

## 💡 Example

```java
@Component
public class MyService {
    @Autowired
    private Coach coach;
}
```

> 🔧 Spring bypasses constructors and setters to inject the dependency straight into the field.

---

## 🕰️ Background

- 📍 **Used frequently** in older Spring projects  
- ⚠️ **Fallen out of favor** in recent years

---

## ⚠️ Drawbacks

- ❌ **Harder to unit test** — dependencies are hidden and can't easily be mocked or replaced
- ❌ Breaks **encapsulation**
- ❌ No way to enforce **required dependencies** at construction time

---

## ✅ Modern Best Practice

> The [spring.io](https://spring.io) team **does not recommend field injection** in new projects.

Use **constructor injection** for required dependencies and **[[setter injection]]** for optional ones.

---

## 🧾 Summary

| 🔍 Aspect         | ✅ Recommended Practice         |
|------------------|---------------------------------|
| Required deps     | Constructor Injection           |
| Optional deps     | [[Setter Injection]]                |
| Legacy support    | Field Injection (read-only)     |

> 🧠 You may still encounter field injection in legacy codebases, but avoid using it in new code.
