# 🔍 Java Reflection  
**Tags:** #java #reflection #advanced

---

## 📌 Definition

**Java Reflection** is an API that allows inspection and manipulation of classes, methods, fields, and constructors **at runtime**, even if they are private.

---

## 💡 Use Cases

- Frameworks like Spring use it for [[Defining Dependency Injection|dependency injection]], **object creation**, and accessing private fields.
- Useful for **dynamic behavior** and **metaprogramming**.

---

## ⚠️ Considerations

- May impact **performance**
- Can **break encapsulation**
- Should be used **cautiously**

```java
Field field = obj.getClass().getDeclaredField("secret");
field.setAccessible(true);
field.set(obj, "newValue");
```

> 🧠 Powerful but should be used with care.
