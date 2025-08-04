# 🔧 Java Local & Instance Variables

**Tags:** #java #variables #oca

Local and instance variables have different scopes, initialization requirements, and modifier restrictions.

---

## 🏠 Local Variables

### 📍 Scope & Definition

```java
public double getPrice(double inputPrice) {
    double margin = 0.05;  // Local variable - defined inside block
    return inputPrice * (1 + margin);
} // margin goes out of scope here
```

**Characteristics:**

- Defined inside code blocks `{}` (for example in [[Defining Methods|methods]])
- Go out of scope when block ends
- Must be explicitly initialized before use

### 🔒 Final Modifier

```java
// ✅ Valid final usage
public double getPrice(double inputPrice) {
    final double margin;
    margin = 0.05;  // Initialize once
    return inputPrice * (1 + margin);
}

// ❌ Cannot reassign final
public double getPrice(double inputPrice) {
    final double margin = 0.05;
    margin = 0.02;  // DOES NOT COMPILE
    return inputPrice * (1 + margin);
}
```

**Rule:** Only one optional modifier allowed - `final`.

### 🎯 Effectively Final

```java
public void process() {
    int count = 5;        // Effectively final
    // count never changes - could add 'final' and still compile
    System.out.println(count);
}
```

**Definition:** Variable that doesn't change value - behaves as if `final`.

---

## 🏢 Instance Variables

### 📊 Class-Level Definition

```java
class Item {
    public double tax = 0.2;     // Instance variable with initialization
    private String name;         // Instance variable - default null
    
    public double getPrice(double inputPrice) {
        double margin = 0.05;    // Local variable
        return inputPrice * (1 + tax) * (1 + margin);
    }
}
```

### 🔧 Access Modifiers

```java
class Product {
    private double cost;      // Only this class
    protected String name;    // Package + subclasses  
    public double tax;        // Everyone
    final String category;    // Also: final, volatile, transient
}
```

### 💾 Default Values

```java
class Defaults {
    int number;        // 0
    double price;      // 0.0
    boolean active;    // false
    String name;       // null
    int[] numbers;     // null
}
```

**Behavior:** Instance variables get default values if not initialized.

---

## 💡 Practical Example

### 🛍️ Complete Class Usage

```java
class Item {
    public double tax = 0.2;  // Instance variable
    
    public double getPrice(double inputPrice) {
        double margin = 0.05;  // Local variable
        return inputPrice * (1 + tax) * (1 + margin);
    }
}

public class MyClass {
    public static void main(String[] args) {
        Item item = new Item();
        System.out.println(item.getPrice(100)); // 126.0
        
        Item specialItem = new Item();
        specialItem.tax = 0.1;  // Modify instance variable
        System.out.println(specialItem.getPrice(100)); // 115.5
    }
}
```

---

## 🔒 Final Reference vs Content

### 📦 [[Arrays|Array]] Example

```java
public void printSomething() {
    final int[] a = {1, 3, 5};  // Reference is final
    a[1] = 7;                   // Content can be modified
    System.out.println(Arrays.toString(a)); // [1, 7, 5]
    
    // a = new int[]{2, 4, 6};  // DOES NOT COMPILE - can't reassign reference
}
```

**Key Point:** `final` makes the reference constant, not the content.

---