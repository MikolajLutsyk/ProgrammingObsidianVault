# 🔗 Java Functional [[Interface Basics|Interfaces]] and Lambdas

**Tags:** #java #functional-interface #lambda #oop #oca

Functional interfaces and lambda expressions provide a concise way to implement single-[[Defining Methods|method]] interfaces.

---

## 🎯 What is a Functional Interface?

A **functional interface** is an interface which has **exactly one [[Abstract Classes|abstract method]]**.

```java
@FunctionalInterface
interface Animal {
    public void speak();        // Exactly one abstract method
}
```

**Key Points:**

- **1️⃣ One abstract method** - Must have exactly one abstract method
- **✅ @FunctionalInterface** - Optional annotation (but recommended)
- **📚 Pre-defined interfaces** - Java provides many (Supplier, Consumer, Predicate, Function, etc.)

---

## 🏗️ Traditional Implementation

### [[Class Basics|Class]] Implementation

```java
@FunctionalInterface
interface Animal {
    public void speak();
}

class Dog implements Animal {
    public void speak() {
        System.out.println("Woof!");
    }
}

public class MyClass {
    public static void main(String args[]) {
        Dog dog = new Dog();
        dog.speak();                    // Output: Woof!
    }
}
```

### Anonymous Class Implementation

```java
@FunctionalInterface
interface Animal {
    public void speak();
}

public class MyClass {
    public static void main(String args[]) {
        Animal dog = new Animal() {     // Anonymous class
            public void speak() {
                System.out.println("Woof!");
            }
        };
        dog.speak();                    // Output: Woof!
    }
}
```

---

## ⚡ Lambda Expression Syntax

**Lambda expressions** provide a concise way to implement functional interfaces:

```java
@FunctionalInterface
interface Animal {
    public void speak();
}

public class MyClass {
    public static void main(String args[]) {
        Animal dog = () -> System.out.println("Woof!");
        dog.speak();                    // Output: Woof!
    }
}
```

**Lambda Syntax:**

- **📝 Parameters** - `()` for no parameters, `(param)` for one, `(a, b)` for multiple
- **➡️ Arrow** - `->` separates parameters from implementation
- **🔧 Implementation** - Single line or block `{ }`

---

## 🔄 Multiple Implementations

You can create different implementations in a single class:

```java
@FunctionalInterface
interface Animal {
    public void speak();
}

public class MyClass {
    public static void main(String args[]) {
        Animal dogImplementation = () -> System.out.println("Woof!");
        Animal catImplementation = () -> System.out.println("Meow!");
        Animal cowImplementation = () -> System.out.println("Moo!");
        
        dogImplementation.speak();      // Output: Woof!
        catImplementation.speak();      // Output: Meow!
        cowImplementation.speak();      // Output: Moo!
    }
}
```

---

## 📊 Parameters and Return Types

Lambda expressions can handle parameters and return values:

```java
@FunctionalInterface
interface Multiplicable {
    public int multiply(int a, int b);
}

public class MyClass {
    public static void main(String[] args) {
        Multiplicable myImplementation = (a, b) -> a * b;
        int result = myImplementation.multiply(3, 4);
        System.out.println(result);     // Output: 12
    }
}
```

---

## 📝 Lambda Syntax Variations

### 🔹 One Parameter

```java
// All equivalent:
n -> 2*n                    // No parentheses needed
(n) -> 2*n                  // Parentheses optional
(int n) -> 2*n              // Explicit type
n -> { return 2*n; }        // Block syntax
(n) -> { return 2*n; }      // Block with parentheses
(int n) -> { return 2*n; }  // Block with type
```

### 🔹 Multiple Parameters

```java
// All equivalent:
(a, b) -> a*b                       // Simple expression
(int a, int b) -> a*b               // With types
(a, b) -> { return a*b; }           // Block syntax
(int a, int b) -> { return a*b; }   // Block with types
```

**Key Rules:**

- **🔍 Single parameter** - Parentheses optional (unless specifying type)
- **🔢 Multiple parameters** - Parentheses required
- **📄 Single expression** - No `return` keyword needed
- **🔧 Block syntax** - Use `{ }` and `return` for multiple statements

---

## 💡 Lambda vs Anonymous Class

|Feature|Lambda Expression|Anonymous Class|
|---|---|---|
|**Syntax**|`() -> implementation`|`new Interface() { method() {...} }`|
|**Length**|Concise|Verbose|
|**Use Case**|Functional interfaces only|Any interface/class|
|**Performance**|Better (no extra class file)|Slower (creates .class file)|

---

## 🎯 Key Takeaways

- **🎯 Functional Interface** - Interface with exactly one abstract method
- **✅ @FunctionalInterface** - Optional but recommended annotation
- **⚡ Lambda Syntax** - `parameters -> implementation`
- **🔄 Multiple implementations** - Create different behaviors easily
- **📊 Flexible parameters** - Handle no params, single param, or multiple params
- **📝 Syntax variations** - Multiple ways to write the same lambda
- **💡 Concise alternative** - Shorter than anonymous classes for functional interfaces

---