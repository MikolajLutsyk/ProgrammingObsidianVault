# 📦 Java Wrapper [[Class Basics|Classes]]

**Tags:** #java #wrapper #oca

Wrapper classes convert primitives to objects, enabling object-only features and providing utility methods.

---

## 🔹 When to Use Wrapper Classes

### 📊 Collections & Generics

```java
List<int> numbers;     // DOES NOT COMPILE - primitives not allowed
List<Integer> numbers; // ✅ Wrapper classes work with generics
```

**Reason:** Collections only work with objects, not primitives.

### 🕳️ Null Values

```java
int age = null;        // DOES NOT COMPILE - primitives can't be null
Integer age = null;    // ✅ Wrapper classes can be null
```

**Use Case:** When you need to represent "no value" or missing data.

### 🔧 Utility [[Defining Methods|Methods]]

```java
String numberStr = "123";
int value = Integer.parseInt(numberStr);  // Static utility method
Integer maxValue = Integer.MAX_VALUE;     // Constants
```

**Benefit:** Access to parsing methods and predefined constants.

### 🌊 Streams & APIs

```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
numbers.stream()
       .filter(n -> n > 3)  // Lambda requires objects
       .collect(Collectors.toList());
```

**Requirement:** Streams, lambdas, and modern APIs expect objects.

---

## 💡 Key Point

**Wrapper classes bridge the gap between Java's primitive types and its object-oriented features.**

---