# 🏊 Java [[String]] Pool & Memory Management

**Tags:** #java #string #memory #pool #intern

The JVM stores string literals in a special memory location called the String Pool (or Intern Pool) to optimize memory usage and improve performance.

---

## 🔹 String Pool Concept

### 💾 Memory Optimization

```java
String name = "John";
String theName = "John";
```

**Memory Layout:**

```
Reference                 String Pool
name       ────────┐
                   ├────► "John"
theName    ────────┘
```

**Efficiency:** Instead of creating duplicate strings, Java reuses the same memory location for identical string literals.

---

## 🕰️ Compile Time vs Runtime

### ⚡ Intern Method (Compile Time)

```java
String str1 = "Hello";           // Automatically interned
String str2 = "Hello";           // Points to same pool location
String str3 = new String("Hello").intern(); // Manually interned
```

**Purpose:** Forces string to be stored in the string pool for memory optimization.

### 🔧 New Keyword (Runtime)

```java
String str1 = new String("Hello"); // Creates new object in heap
String str2 = new String("Hello"); // Creates another new object
```

**Behavior:** Creates new String objects in heap memory, bypassing the string pool.

---

## 🔗 Interning vs Referencing

### 🎯 Interning

```java
String str1 = "Java";
String str2 = "Java";           // Same reference due to interning
String str3 = new String("Java").intern(); // Forced into pool

System.out.println(str1 == str2); // true - same pool reference
System.out.println(str1 == str3); // true - interned to same location
```

**Definition:** A mechanism Java uses to optimize memory usage for strings by storing unique literals in a shared pool.

### 👉 Referencing

```java
String original = "Hello";
String reference = original;    // Points to same object

System.out.println(original == reference); // true - same reference
```

**Definition:** Assigning one variable to refer to an object — it's about pointing to the same memory location.

---

## 💡 Memory Comparison

### 🏊 String Pool Behavior

```java
String a = "Hello";
String b = "Hello";
String c = "Hel" + "lo";        // Compile-time concatenation

System.out.println(a == b);     // true - pool reference
System.out.println(a == c);     // true - compile-time optimization
```

### 🆕 Heap Memory Behavior

```java
String x = new String("Hello");
String y = new String("Hello");
String z = "Hello";

System.out.println(x == y);     // false - different heap objects
System.out.println(x == z);     // false - heap vs pool
System.out.println(x.equals(z)); // true - same content
```

---