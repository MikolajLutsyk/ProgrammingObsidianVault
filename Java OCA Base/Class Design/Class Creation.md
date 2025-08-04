# 🏗️ Java [[Class Basics|Class]] Creation 

**Tags:** #java #class #inheritance #oop #oca

How to create and implement inheritance between classes in Java, with practical examples of member access.

---

## 🎯 Basic [[Inheritance]] Example

### 📁 Parent Class (Mammal.java)

```java
public class Mammal {
    private int age;           // Private - only accessible within Mammal
    protected String name;     // Protected - accessible to subclasses
    
    public int getAge() { 
        return age; 
    }
    
    public void setAge(int theAge) { 
        age = theAge; 
    }
}
```

### 🐕 Child Class (Dog.java)

```java
public class Dog extends Mammal {
    protected void setNameAndAge(String dogName, int age) {
        name = dogName;        // ✅ Inherited from Mammal (protected)
        setAge(age);          // ✅ Inherited from Mammal (public method)
    }
    
    public void barks() {
        System.out.println("Dog " + name + " (" + getAge() + ") says: woof!");
    }
    
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setNameAndAge("Rex", 5);
        dog.barks();
        // Output: Dog Rex (5) says: woof!
    }
}
```

---

## 📂 File Organization

### 🔍 Multiple Classes in One File

- If one class is **not public**, both classes can be in the same file
- Example: `Dog.java` can contain both `Dog` and non-public `Mammal`

```java
// Dog.java
class Mammal { /* ... */ }        // Not public
public class Dog extends Mammal { /* ... */ }
```

---

## 🔍 The `this` Keyword

Used to access members of the **current class** to resolve naming conflicts.

### ❌ Without `this` (different parameter name)

```java
public void setAge(int theAge) {
    age = theAge;              // Clear - no conflict
}
```

### ✅ With `this` (same parameter name)

```java
public void setAge(int age) {
    this.age = age;            // this.age = instance variable
}                              // age = parameter
```

### 🔍 Variable Resolution Priority

Java looks for variables in this order:

1. **Local variables** (method parameters/variables)
2. **Instance variables** (if no local variable found)

---

## 🔼 The `super` Keyword

Used to access members of the **superclass** explicitly.

### 🎯 Without `super` (implicit access)

```java
protected void setNameAndAge(String dogName, int age) {
    name = dogName;            // Accesses inherited field
    setAge(age);              // Calls inherited method
}
```

### 🎯 With `super` (explicit access)

```java
protected void setNameAndAge(String name, int age) {
    super.name = name;         // Explicitly access superclass field
    setAge(age);              // Same as super.setAge(age)
}
```

---

## 💡 Key Inheritance Points

- **🔒 private members** - Not accessible to subclasses
- **🛡️ protected members** - Accessible to subclasses
- **🌍 public members** - Accessible everywhere
- **📦 Methods** - Inherited and can be called directly
- **🏷️ Fields** - Inherited based on access modifiers

### 🎯 Access Summary

```java
// In Dog class:
name = "Buddy";        // ✅ Protected field from Mammal
setAge(3);            // ✅ Public method from Mammal  
// age = 3;           // ❌ Private field - not accessible
getAge();             // ✅ Public method to access private field
```

---