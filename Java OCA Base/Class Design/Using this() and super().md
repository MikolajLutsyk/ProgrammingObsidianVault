# 🔗 Java Constructor Chaining - `this()` and `super()`

**Tags:** #java #constructors #this #super #inheritance #constructor-chaining

Special methods to call other constructors within the same class (`this()`) or parent class (`super()`).

---

## 🔄 Using `this()` - [[Creating Constructors|Constructor]] Chaining

**`this()`** calls another constructor in the **same [[Class Basics|class]]**.

```java
public class Dog {
    private String name;
    private int age;
    
    public Dog(String name, int age) {      // Main constructor
        this.name = name;
        this.age = age;
    }
    
    public Dog() {                          // No-arg constructor
        this("Chip", 1);                    // Calls other constructor
        System.out.println("Woof!");
    }
}

Dog dog = new Dog();
// Output: Woof!
// Result: Name: Chip, Age: 1
```

**Benefits:**

- **Reduces code duplication** - Reuse initialization logic
- **Centralizes initialization** - Main logic in one constructor
- **Maintains consistency** - All objects initialized the same way

---

## ⚠️ Rules for `this()`

### 1️⃣ **First Line Only**

```java
public Dog() {
    System.out.println("Woof!");  // ❌ Other code first
    this("Chip", 1);              // ❌ DOES NOT COMPILE
}
```

### 2️⃣ **Call Only Once**

```java
public Dog() {
    this("Chip", 1);    // ❌ First call
    this("Max", 2);     // ❌ DOES NOT COMPILE - Second call
}
```

### 3️⃣ **Avoid Cycles**

```java
public Dog() {
    this();            // ❌ Calls itself - INFINITE LOOP
}

// Or indirect cycle:
public Dog() {
    this("Chip", 1);
}
public Dog(String name, int age) {
    this();            // ❌ Calls back to Dog() - CYCLE
}
```

---

## 🔼 Using `super()` - [[Inheritance|Parent]] Constructor

**`super()`** calls a constructor in the **parent class**.

```java
class Mammal {
    public int age;
    
    public Mammal(int age) {
        this.age = age;
    }
}

public class Dog extends Mammal {
    private String name;
    
    public Dog(String name, int age) {
        super(age);                    // Call parent constructor
        this.name = name;
        System.out.println("Woof!");
    }
}
```

---

## 🤖 Automatic `super()` Insertion

**If no `this()` or `super()` is specified**, the compiler automatically inserts `super()`:

### ✅ Works (Parent has no-arg constructor)

```java
class Mammal {
    public int age;
    // Compiler creates: public Mammal() { }
}

public class Dog extends Mammal {
    public Dog() {
        // Compiler inserts: super();
        System.out.println("Woof!");
    }
}
```

### ❌ Compilation Error (No parent no-arg constructor)

```java
class Mammal {
    public int age;
    
    public Mammal(int age) {          // Custom constructor exists
        this.age = age;               // No default constructor created!
    }
}

public class Dog extends Mammal {
    public Dog() {
        // Compiler tries to insert: super();
        // But Mammal() doesn't exist!
        System.out.println("Woof!");  // ❌ DOES NOT COMPILE
    }
}
```

**Solution:** Explicitly call `super(value)` with required parameters.

---

## 📋 Rules for `super()`

### 1️⃣ **Auto-Insertion**

- If no explicit `this()` or `super()` → compiler inserts `super()`
- Happens in **every constructor** automatically

### 2️⃣ **First Line Only**

```java
public Dog(String name, int age) {
    this.name = name;    // ❌ Other code first
    super(age);          // ❌ DOES NOT COMPILE
}
```

### 3️⃣ **Call Only Once**

```java
public Dog(String name, int age) {
    super(age);          // ❌ First call
    super(age + 1);      // ❌ DOES NOT COMPILE - Second call
}
```

---

## 🎯 Constructor Call Order

When creating objects, constructors are called in this order:

1. **🔼 Parent constructor** (via `super()`)
2. **🔽 Current constructor** body
3. **📝 Any additional initialization**

```java
// Example execution flow:
Dog dog = new Dog("Rex", 5);

// 1. super(5) → Mammal constructor runs
// 2. this.name = "Rex" → Dog constructor runs  
// 3. System.out.println("Woof!") → Additional code
```

---

## 💡 Key Takeaways

- **🔄 `this()`**: Calls another constructor in same class
- **🔼 `super()`**: Calls parent class constructor
- **📍 Position**: Both must be **first line** of constructor
- **1️⃣ Frequency**: Can only call **once** per constructor
- **🤖 Auto-insertion**: `super()` added automatically if neither is specified
- **⚠️ Watch out**: Ensure parent has accessible no-arg constructor or call `super()` explicitly

---