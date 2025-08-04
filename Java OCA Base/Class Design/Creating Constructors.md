# 🔧 Java Constructors

**Tags:** #java #constructor #oop #oca

Special [[Defining Methods|methods]] that initialize objects when they're created using the `new` keyword.

---

## 🎯 Constructor Basics

**Constructors** are special methods called automatically when creating object instances.

```java
public class Dog {
    public Dog() {                    // Constructor
        System.out.println("Woof!");
    }
}

Dog dog = new Dog();  // Output: "Woof!"
```

### 📋 Constructor Rules

- **🏷️ Name** must match the class name exactly
- **🚫 No return type** (not even `void`)
- **🔄 Called automatically** when using `new`

---

## 🔄 Constructor Overloading

You can have multiple constructors with different parameters:

```java
public class Dog {
    private String name;
    private int age;
    
    public Dog() {                           // No-argument constructor
        System.out.println("Woof!");
    }
    
    public Dog(String name, int age) {       // Parameterized constructor
        this.name = name;
        this.age = age;
    }
    
    public Dog(String name) {                // Single parameter constructor
        this.name = name;
    }
}
```

**Usage:**

- `new Dog()` → calls no-argument constructor
- `new Dog("Rex", 5)` → calls two-parameter constructor
- `new Dog("Buddy")` → calls single-parameter constructor

---

## 🏭 Default Constructor

### ✅ Auto-Generated (when no constructors exist)

```java
class Dog {
    public String name;
    // Compiler automatically creates: public Dog() { }
}

Dog dog = new Dog();  // ✅ Works - uses default constructor
```

### ❌ Not Generated (when constructors exist)

```java
class Dog {
    public Dog(String name) { /* ... */ }   // Custom constructor exists
    // No default constructor created!
}

Dog dog = new Dog();      // ❌ DOES NOT COMPILE
Dog dog = new Dog("Rex"); // ✅ Works
```

**Key Point:** Default constructor only created when **no other constructors** are defined.

---

## 🔐 Constructor Access Modifiers

Constructors can have different visibility levels:

### 🌍 Public (Most Common)

```java
public Dog() { }  // Anyone can create Dog objects
```

### 🛡️ Protected/Package-Private

```java
protected Dog() { }  // Only subclasses and same package
```

### 🔒 Private (Special Cases)

```java
private Dog() { }  // Cannot use 'new' from outside class
```

**Private constructors** are used for:

- **Singleton patterns** - Only one instance allowed
- **Utility classes** - Prevent instantiation
- **Factory methods** - Control object creation

### 💡 Factory Method Example

```java
public class LocalDate {
    private LocalDate() { }  // Private constructor
    
    public static LocalDate now() {      // Static factory method
        return new LocalDate();          // Internal creation
    }
}

// Usage:
LocalDate date = LocalDate.now();        // ✅ Via factory method
// LocalDate date = new LocalDate();     // ❌ Constructor is private
```

---

## 🎯 Key Takeaways

- **🔧 Purpose**: Initialize object state when created
- **📛 Naming**: Must match class name exactly
- **🚫 Return**: No return type allowed
- **🔄 Overloading**: Multiple constructors with different parameters
- **🏭 Default**: Auto-generated only if no custom constructors exist
- **🔐 Access**: Can be public, protected, package-private, or private

---