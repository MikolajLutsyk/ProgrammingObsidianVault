# 🔍 Java Predicates with [[Functional Interfaces and Lambdas|Lambda Expressions]]
**Tags:** #java #lambda #predicate #oop #oca

Predicate is a pre-defined functional interface that enables boolean testing with lambda expressions.

---

## 🎯 What is Predicate?

**Predicate** is a pre-defined functional interface provided by Java that represents a boolean-valued function of one argument.

**Key Characteristics:**

- **📦 Package:** `java.util.function` (must be imported)
- **🔧 Abstract Method:** `test(T t)` - takes argument of type T and returns boolean
- **✅ Annotation:** `@FunctionalInterface`

### 🏗️ [[Interface Basics|Interface]] Definition

```java
@FunctionalInterface
public interface Predicate<T> {
    boolean test(T t);
    // ... default and static methods
}
```

---

## ⚡ Basic Implementation

To use Predicate, you must implement the `test(T)` method using lambda expressions:

```java
import java.util.function.*;

public class MyClass {
    public static void main(String[] args) {
        // Lambda implementation: for given n, return n > 10
        Predicate<Integer> gt10 = n -> n > 10;
        
        System.out.println(gt10.test(7));   // Output: false
        System.out.println(gt10.test(12));  // Output: true
    }
}
```

**🔍 Lambda Breakdown:**

- **📝 Parameter:** `n` - input value to test
- **➡️ Arrow:** `->` separates parameter from logic
- **🔧 Implementation:** `n > 10` - returns boolean result

---

## 🚀 Advanced Usage with [[Defining Methods|Method]] Parameters

You can pass Predicate as a parameter to methods for flexible testing:

```java
import java.util.function.*;

public class MyClass {
    // 🔧 Method that accepts a Predicate for testing
    static void myProbe(int n, Predicate<Integer> predicate) {
        if (predicate.test(n)) {
            System.out.println("The test has passed.");
        } else {
            System.out.println("The test has failed.");
        }
    }
    
    public static void main(String args[]) {
        // ✅ Test if 5 > 2
        myProbe(5, n -> n > 2);                    // Output: The test has passed.
        
        // ❌ Test if 5 is even
        myProbe(5, n -> n % 2 == 0);               // Output: The test has failed.
        
        // 🔄 Create a reusable predicate: n² + 5 > 100
        Predicate<Integer> myCriterium = n -> n*n + 5 > 100;
        
        myProbe(7, myCriterium);   // 7² + 5 = 54 > 100? ❌ The test has failed.
        myProbe(11, myCriterium);  // 11² + 5 = 126 > 100? ✅ The test has passed.
    }
}
```

---

## 📊 Common Predicate Patterns

### 🔹 Simple Comparisons

```java
Predicate<Integer> isPositive = n -> n > 0;
Predicate<Integer> isEven = n -> n % 2 == 0;
Predicate<String> isEmpty = s -> s.isEmpty();
```

### 🔹 Complex Logic

```java
Predicate<Integer> isValidAge = age -> age >= 0 && age <= 150;
Predicate<String> isValidEmail = email -> email.contains("@") && email.contains(".");
Predicate<Double> inRange = value -> value >= 10.0 && value <= 100.0;
```

### 🔹 Mathematical Operations

```java
Predicate<Integer> isPerfectSquare = n -> {
    int sqrt = (int) Math.sqrt(n);
    return sqrt * sqrt == n;
};
```

---

## 💡 Lambda Syntax Variations for Predicates

### 🔹 Single Line Expression

```java
// All equivalent:
Predicate<Integer> gt10 = n -> n > 10;           // Simple
Predicate<Integer> gt10 = (n) -> n > 10;         // With parentheses
Predicate<Integer> gt10 = (Integer n) -> n > 10; // With type
```

### 🔹 Block Syntax

```java
Predicate<Integer> complexTest = n -> {
    System.out.println("Testing: " + n);
    return n > 10 && n % 2 == 0;
};
```

---

## 🎯 Key Benefits

|Benefit|Description|
|---|---|
|**🔄 Reusability**|Predicates can be stored in variables and reused|
|**🚀 Flexibility**|Can be passed as parameters to methods|
|**📖 Readability**|Lambda syntax makes code more concise and readable|
|**🛡️ Type Safety**|Generics ensure type safety at compile time|
|**⚡ Performance**|No extra class files created (unlike anonymous classes)|

---

## 🔧 Common Use Cases

- **🔍 Filtering** - Use with streams to filter collections
- **✅ Validation** - Check if [[Initializing objects|objects]] meet certain criteria
- **🔀 Conditional Logic** - Replace complex if-else statements
- **🧪 Testing** - Create reusable test conditions
- **📊 Data Processing** - Test elements in collections

---

## 🎯 Key Takeaways

- **🔍 Predicate Interface** - Takes one argument of type T, returns boolean
- **📦 Import Required** - Must import `java.util.function.*`
- **⚡ Lambda Implementation** - Use `parameter -> boolean_expression` syntax
- **🔄 Reusable Logic** - Store predicates in variables for reuse
- **🚀 Method Parameters** - Pass predicates to methods for flexible testing
- **📊 Functional Programming** - Enables functional programming patterns in Java
- **💡 Concise Alternative** - Much shorter than traditional implementations

---