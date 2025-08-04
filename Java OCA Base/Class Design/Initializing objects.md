# ⚡ Java Object Initialization Order

**Tags:** #java #initialization #oop #oca

Understanding the precise order in which Java initializes classes and creates objects.

---

## 🏗️ [[Class Basics|Class]] Initialization Order

**When a class is first loaded**, Java follows this sequence:

1. **🔼 Initialize superclass** (if exists and not already initialized)
2. **📊 Process static variables** (in order of appearance)
3. **🔧 Process static initializers** (in order of appearance)

**⚠️ Important:** This happens **at most once** per class during the program's lifetime.

### 💡 Class Initialization Triggers

- **🎯 main() method** inside the class
- **🆕 First object creation** with `new`
- **📊 Accessing static members**

### 📝 Example

```java
class Mammal {
    static { System.out.println("Hello."); }        // Static initializer
}

public class Dog extends Mammal {
    static { System.out.println("Woof!"); }         // Static initializer
    
    public static void main(String[] args) {
        System.out.println("Good afternoon.");
        new Dog();  // First object creation
        new Dog();  // No additional class initialization
        new Dog();  // No additional class initialization
    }
}
```

**Output:**

```
Hello.           ← Mammal static initializer (superclass first)
Woof!            ← Dog static initializer
Good afternoon.  ← main() method execution
```

**Notice:** Static initialization happens only once, not for each object.

---

## 🎯 Instance Initialization Order

**When creating an object instance**, Java follows this sequence:

1. **🏗️ Initialize class** (if not already done)
2. **🔼 Initialize superclass instance** (if exists)
3. **📋 Process instance variable declarations** (in order of appearance)
4. **🔧 Process instance initializers** (in order of appearance)
5. **🎯 Execute constructor**

### 📝 Complete Example

```java
class Mammal {
    static { System.out.println("Hello!"); }              // 1. Static init
    { System.out.println("Good Afternoon."); }            // 4. Instance init
}

public class Dog extends Mammal {
    private String name = "Rex";                           // 3. Instance variable
    { System.out.println("Name: " + name); }              // 4. Instance init
    
    private static int i = 0;                              // 1. Static variable
    static { System.out.println(i); }                     // 1. Static init
    
    { 
        i++; 
        System.out.println(i); 
    }                                                      // 4. Instance init
    
    public Dog() {                                         // 5. Constructor
        System.out.println("Woof!");
    }
    
    public static void main(String[] args) {
        System.out.println("I am the main one.");
        Dog dog = new Dog();
    }
}
```

**Output:**

```
Hello!              ← Mammal static initializer
0                   ← Dog static initializer (i = 0)
I am the main one.  ← main() method
Good Afternoon.     ← Mammal instance initializer
Name: Rex           ← Dog instance variable + initializer
1                   ← Dog instance initializer (i++)
Woof!               ← Dog constructor
```

---

## 🔒 Final Variables and Initialization

**Final instance variables** must be assigned a value by the time the constructor completes.

### ✅ Valid Approaches

```java
public class Item {
    private final double TAX;
    private final double price;
    
    public Item() {
        this.price = 12.5;    // Assignment in constructor
    }
    
    {
        TAX = 0.2;            // Assignment in instance initializer
    }
}
```

**Why this works:**

- Instance initializers run **before** constructors
- Both approaches complete before constructor finishes
- Final variables get their values within the required timeframe

### ❌ Invalid Example

```java
public class Item {
    private final double TAX;    // ❌ Never assigned - DOES NOT COMPILE
    
    public Item() {
        // TAX never gets a value
    }
}
```

---

## 📊 Initialization Summary

### 🏗️ Class-Level (Once per class)

1. **Superclass static** initialization
2. **[[Static members|Static variables]]** (declaration order)
3. **Static initializers** (declaration order)

### 🎯 Instance-Level (Every object creation)

1. **Class initialization** (if needed)
2. **Superclass instance** initialization
3. **Instance variables** (declaration order)
4. **Instance initializers** (declaration order)
5. **Constructor** execution

### 🔑 Key Points

- **📅 Order matters** - Declaration order determines execution sequence
- **1️⃣ Static once** - Class initialization happens only once
- **🔄 Instance always** - Instance initialization happens for every object
- **🔼 Parents first** - Superclass always initializes before subclass
- **🔒 Final deadline** - Final variables must be set by constructor completion

---