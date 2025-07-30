# 🔐 Java Access Modifiers Reference
**Tags:** #java #access-modifiers #visibility #encapsulation

Access modifiers control the visibility and accessibility of classes, methods, and fields in Java.

---

## 🔹 Access Levels

### 🔒 Private
```java
class Dog {
    private String genus = "Canis";  // Only within this class
}
```
**Scope:** Only within the class where declared.

### 📦 Default (Package-Private)
```java
class Dog {
    String genus = "Canis";  // No keyword - package access
}
```
**Scope:** Within the same package only.

### 🛡️ Protected
```java
class Dog {
    protected String genus = "Canis";  // Package + inheritance
}
```
**Scope:** Same package + subclasses (even in different packages).

### 🌍 Public
```java
class Dog {
    public String genus = "Canis";  // Everywhere
}
```
**Scope:** Accessible from anywhere in the program.

---

## ❌ Private Access Example

### 🚫 Direct Access Fails
```java
class Dog {
    private String genus = "Canis";
}

public class MyClass {
    public static void main(String[] args) {
        Dog dog = new Dog();
        System.out.println(dog.genus); // DOES NOT COMPILE
    }
}
```

### ✅ Access Through Public Method
```java
class Dog {
    private String genus = "Canis";
    
    public void printGenus() {
        System.out.println("Genus: " + genus); // OK - same class
    }
}

public class MyClass {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.printGenus(); // Outputs: Genus: Canis
    }
}
```

---

## 📦 Default Access Example

### 🏠 Same Package Access
```java
// Dog.java
package zoo.dogs;
public class Dog {
    String genus = "Canis";  // Default access
}

// MyClass.java  
package zoo.dogs;
public class MyClass {
    public static void main(String[] args) {
        Dog dog = new Dog();
        System.out.println(dog.genus); // OK - same package
        // Outputs: Canis
    }
}
```

---

## 🛡️ Protected Access Example

### 👨‍👦 Inheritance Access
```java
// Dog.java
package zoo.dogs;
public class Dog {
    protected String genus = "Canis";
}

// Husky.java
package zoo.huskies;  // Different package
import zoo.dogs.*;

public class Husky extends Dog {
    public static void main(String[] args) {
        Husky husky = new Husky();
        System.out.println(husky.genus); // OK - subclass access
        // Outputs: Canis
    }
}
```

---

## 📊 Access Summary

| Modifier | Same Class | Same Package | Subclass | Everywhere |
|----------|------------|--------------|----------|------------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| default | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

---