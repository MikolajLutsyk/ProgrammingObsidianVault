# 🔤 String Definition

**Tags:** #java #string #definition

**String** is a sequence of characters in Java, implementing the `CharSequence` interface. It represents immutable text data and is one of the most fundamental classes in Java programming.

---

## 🔹 Key Characteristics

### 🔒 Immutable

```java
String str = "Hello";
str.toUpperCase(); // Returns new String, original unchanged
```

**Behavior:** Cannot be changed after creation - methods return new String objects.

### 📝 Sequence of Characters

```java
String name = "John"; // Ordered collection: 'J', 'o', 'h', 'n'
```

**Structure:** Ordered collection of char values with defined positioning.

### 🔗 Implements CharSequence

```java
CharSequence text = "Hello World"; // String can be assigned to CharSequence
```

**Interface:** Provides standard text manipulation and access methods.

### 💾 Reference Type

```java
String str1 = "Hello";
String str2 = "Hello"; // May reference same object (string pool)
```

**Memory:** Stored in heap memory, string literals use string pool for efficiency.

---