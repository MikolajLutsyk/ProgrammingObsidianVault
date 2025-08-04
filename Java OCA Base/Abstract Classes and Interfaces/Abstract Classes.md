# 🎭 Java Abstract [[Class Basics|Classes]] and [[Defining Methods|Methods]]

**Tags:** #java #abstract #inheritance #oop #oca

Abstract classes provide templates that must be extended but cannot be instantiated directly.

---

## 🏗️ Abstract Classes

**Abstract classes** can be extended but **cannot be instantiated**.

```java
public abstract class Mammal { }        // Abstract class
public class Dog extends Mammal { }     // Concrete class

Dog dog = new Dog();                    // ✅ OK - concrete class
Mammal mammal = new Mammal();           // ❌ NOK - cannot instantiate abstract
```

**Key Points:**

- **🔧 Template role** - Defines common structure for subclasses
- **🚫 No instantiation** - Cannot create objects directly
- **✅ [[Inheritance]] required** - Must be extended by concrete classes

---

## 🎯 Abstract Methods

**Abstract methods** have no implementation - subclasses must provide the body.

```java
public abstract class Mammal {
    public abstract void speak();       // No body - just declaration
}

public class Dog extends Mammal {
    @Override
    public void speak() {               // Must implement
        System.out.println("Woof!");
    }
}

public class Cat extends Mammal {
    @Override
    public void speak() {               // Must implement
        System.out.println("Meow");
    }
}
```

**Benefits:**

- **📋 Enforces contract** - Guarantees all subclasses implement required methods
- **🎭 Enables polymorphism** - Common interface with different implementations
- **🏗️ Design consistency** - Standardizes method signatures across subclasses

---

## 📋 Abstract Method Rules

### 1️⃣ **Instance Methods Only**

```java
public abstract class Example {
    public abstract void method();           // ✅ Instance method
    // public abstract static void method(); // ❌ Static not allowed
    // private abstract int field;          // ❌ Variables not allowed
}
```

### 2️⃣ **Must be in Abstract Class**

```java
public abstract class Animal {              // ✅ Abstract class
    public abstract void speak();           // ✅ Abstract method allowed
}

public class Dog {                          // ❌ Concrete class
    // public abstract void speak();        // ❌ Abstract method not allowed
}
```

### 3️⃣ **Concrete Subclasses Must Implement All**

```java
abstract class Animal {
    public abstract void speak();
}

abstract class Mammal extends Animal {      // Abstract - can skip implementation
    public abstract void walks();
}

public class Dog extends Mammal {           // Concrete - must implement ALL
    @Override
    public void speak() {                   // From Animal
        System.out.println("Woof!");
    }
    
    @Override
    public void walks() {                   // From Mammal
        System.out.println("Dog walks.");
    }
}
```

### 4️⃣ **Overriding Rules Apply**

- Same signature required
- Access level must be equal or more accessible
- Exception handling rules apply
- Covariant return types allowed

---

## 🔗 Abstract Class Inheritance Chain

```java
abstract class Animal {
    public abstract void speak();
}

abstract class Mammal extends Animal {
    public abstract void walks();
    // Note: speak() is still abstract here
}

public class Dog extends Mammal {
    // Must implement BOTH abstract methods:
    @Override
    public void speak() { System.out.println("Woof!"); }
    
    @Override
    public void walks() { System.out.println("Dog walks."); }
}
```

**Key Point:** First **concrete class** must implement **all inherited abstract methods**.

---

## 💡 Important Considerations

### 🔧 **Constructors Allowed**

```java
public abstract class Mammal {
    protected String name;
    
    public Mammal(String name) {            // ✅ Abstract classes can have constructors
        this.name = name;
    }
}

public class Dog extends Mammal {
    public Dog(String name) {
        super(name);                        // Must call using super()
    }
}
```

### 🚫 **Invalid Combinations**

```java
public abstract class Example {
    // ❌ Abstract + final = contradiction
    // public abstract final void method();
    
    // ❌ Abstract + private = cannot be overridden
    // private abstract void method();
    
    // ❌ Abstract + static = static methods cannot be overridden
    // public abstract static void method();
}
```

**Why these don't work:**

- **🔒 final** - Cannot be overridden (defeats purpose of abstract)
- **🔐 private** - Cannot be accessed by subclasses to implement
- **🏠 static** - Belongs to class, cannot be overridden

---

## 🎯 Abstract vs Concrete Classes

|Feature|Abstract Class|Concrete Class|
|---|---|---|
|**Instantiation**|❌ Cannot create objects|✅ Can create objects|
|**Abstract Methods**|✅ Can have abstract methods|❌ Cannot have abstract methods|
|**Concrete Methods**|✅ Can have regular methods|✅ Can have regular methods|
|**Constructors**|✅ Can have constructors|✅ Can have constructors|
|**Inheritance**|✅ Can be extended|✅ Can be extended|

---

## 💡 Key Takeaways

- **🎭 Purpose** - Abstract classes define contracts that subclasses must fulfill
- **🚫 No instantiation** - Cannot create objects from abstract classes directly
- **📋 Implementation required** - Concrete subclasses must implement all abstract methods
- **🔧 Constructors allowed** - But only accessible via `super()` from subclasses
- **⚠️ Logical restrictions** - Cannot combine abstract with final, private, or static
- **🏗️ Design tool** - Use when you want to share code but force implementation of specific methods

---