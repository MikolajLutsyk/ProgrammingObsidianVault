# 🧬 Java Inheritance

**Tags:** #java #inheritance #oop #oca

Inheritance allows [[Class Basics|classes]] to inherit members (fields and methods) from other classes, creating parent-child relationships.

---

## 🌳 Basic Inheritance

```java
public class Animal { }
public class Dog extends Animal { }
```

- **🔼 Animal** = **Superclass** (parent)
- **🔽 Dog** = **Subclass** (child)
- Dog **inherits** all accessible members from Animal

---

## 🔗 Transitive Inheritance

Inheritance works through multiple levels:

```java
public class Animal { }
public class Mammal extends Animal { }
public class Dog extends Mammal { }
```

- **Dog** inherits from **Animal**, but only **through** **Mammal**
- Creates inheritance chain: `Dog → Mammal → Animal`

---

## 🚫 Single Inheritance Rule

**Java supports ONLY single inheritance:**

```java
public class Dog extends Animal { }        // ✅ Valid
// public class Dog extends Animal, Plant { } // ❌ Not allowed
```

- Each class can have **only ONE direct superclass**
- Unlike C++ which allows multiple inheritance
- **But:** Classes can implement **multiple interfaces**

---

## 🏷️ Class Modifiers

Classes can have various modifiers that affect inheritance:

- **🔒 `final`** - Cannot be extended
- **🔧 `abstract`** - Must be extended, cannot be instantiated
- **🏠 `static`** - Nested static classes
- **🔐 `sealed`** - Restricts which classes can extend (Java 17+)
- **🔓 `non-sealed`** - Reopens sealed inheritance (Java 17+)

---

## 👑 Object Class - The Ultimate Parent

**Every Java class implicitly inherits from `java.lang.Object`:**

```java
public class Dog { }
// Is equivalent to:
public class Dog extends java.lang.Object { }
```

### 🎯 Key Points

- **Object** is the **only class** without a parent
- **All classes** inherit Object's methods:
    - `toString()` - String representation
    - `equals()` - Equality comparison
    - `hashCode()` - Hash value
    - `getClass()` - Runtime class info
    - And more...

### 💡 Example

```java
Dog myDog = new Dog();
System.out.println(myDog.toString());  // Inherited from Object
System.out.println(myDog.getClass());  // Inherited from Object
```

---