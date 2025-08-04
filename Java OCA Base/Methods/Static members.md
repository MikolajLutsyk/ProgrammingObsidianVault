# ⚡ Java Static Members

**Tags:** #java #static #oca

Static members belong to the class rather than individual instances, providing shared data and behavior across all instances.

---

## 🔹 Static Variables

### 🏢 [[Class Basics|Class]]-Level Sharing

```java
class Item {
    public static double tax = 0.2;  // Shared by all instances
    
    public double getPrice(double inputPrice) {
        return inputPrice * (1 + tax);
    }
}

Item item1 = new Item();
Item item2 = new Item();
item2.tax = 0.1;  // Changes for ALL instances

System.out.println(item1.getPrice(100)); // 110.0 (uses new tax value)
```

**Behavior:** One copy shared by all instances of the class.

---

## 🔧 Static [[Defining Methods|Methods]]

### 📞 Direct Class Access

```java
class Dog {
    public static void bark() {
        System.out.println("Woof!");
    }
}

// Preferred way
Dog.bark();  // Direct class access

// Also valid
Dog dog = new Dog();
dog.bark();  // Instance access (not recommended)
```

---

## ⚠️ Static Method Restrictions

### 🚫 Cannot Access Non-Static Directly

```java
class MyClass {
    String hi = "Good Afternoon!";  // Non-static field
    
    public static void greet() {
        System.out.println(hi);  // DOES NOT COMPILE
    }
}
```

### ✅ Three Solutions

#### 1️⃣ Make Field Static

```java
static String hi = "Good Afternoon!";
```

#### 2️⃣ Create Instance Per Call

```java
public static void greet() {
    System.out.println(new MyClass().hi);
}
```

#### 3️⃣ Use Shared Instance

```java
class MyClass {
    String hi = "Good Afternoon!";
    static MyClass instance = new MyClass();
    
    public static void greet() {
        System.out.println(instance.hi);
    }
}
```

---

## 🔒 Static Final Constants

### 📝 Standard Constants

```java
public class Item {
    public static final double VALUE_ADDED_TAX = 0.25;  // SNAKE_CASE convention
    
    public double calculatePrice(double price) {
        return price + price * VALUE_ADDED_TAX;
    }
}
```

### 🔧 Static Block Initialization

```java
public class Item {
    public static final double VALUE_ADDED_TAX;
    
    static {  // Static block - runs once when class loads
        VALUE_ADDED_TAX = 0.25;
    }
}
```

---

## 🧮 Complex Static Initialization

### 📊 Multiple Static Blocks

```java
public class MetalBlock {
    public static final double MASS_IN_KILOS;
    public static final double VOLUME_IN_CUBIC_METERS;
    public static final double DENSITY_IN_KILOS_PER_CUBIC_METER;
    
    static {  // Block 1
        MASS_IN_KILOS = 100;
        VOLUME_IN_CUBIC_METERS = 0.01;
    }
    
    static {  // Block 2 - can use values from block 1
        DENSITY_IN_KILOS_PER_CUBIC_METER = MASS_IN_KILOS / VOLUME_IN_CUBIC_METERS;
    }
}
```

**Execution:** Static blocks run in order when class first loads.

---

## 📥 Static Imports

### 🔗 Import Static Methods

```java
// Without static import
System.out.println(Math.pow(2, 5));

// With static import
import static java.lang.Math.pow;
System.out.println(pow(2, 5));
```

### ❌ Import Order Matters

```java
static import java.lang.Math.pow;  // DOES NOT COMPILE - wrong order
import static java.lang.Math.pow;  // ✅ Correct - import keyword first
```

**Rule:** `import` keyword must come before `static`.

---