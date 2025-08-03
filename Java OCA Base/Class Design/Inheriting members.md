# 🔄 Java Inheriting Members - Method Overriding

**Tags:** #java #inheritance #overriding #polymorphism #method-hiding

How subclasses can inherit, override, and hide methods from their parent [[Class Basics|classes]].

---

## 🎯 [[Defining Methods|Methods]] Overriding Basics

**Method overriding** allows subclasses to provide new implementations for inherited methods.

```java
class Mammal {
    public void speak() {
        System.out.println("Mammal is making a sound.");
    }
}

public class Dog extends Mammal {
    @Override                           // Optional but recommended
    public void speak() {               // Same signature
        System.out.println("Woof!");
    }
}

// Usage:
Mammal mammal = new Mammal();
Dog dog = new Dog();
mammal.speak();  // Output: "Mammal is making a sound."
dog.speak();     // Output: "Woof!"
```

**Key Concepts:**

- **🎭 Polymorphism** - Objects can take many forms
- **📝 Same signature** - Method name and parameters must match
- **✅ @Override annotation** - Optional but prevents mistakes

---

## 🔼 Using `super` in Overridden Methods

Access the parent's implementation with `super`:

```java
public class Dog extends Mammal {
    @Override
    public void speak() {
        System.out.println("Woof!");
        super.speak();              // Call parent method
    }
}

dog.speak();
// Output:
// Woof!
// Mammal is making a sound.
```

**Benefits:**

- **🔄 Extend behavior** instead of completely replacing it
- **📚 Reuse parent logic** while adding new functionality

---

## 📋 Method Overriding Rules

### 1️⃣ **Same Signature**

```java
// Parent method:
public void speak() { }

// Override must match exactly:
@Override
public void speak() { }  // ✅ Same name, same parameters
```

### 2️⃣ **Access Level (Equal or More Accessible)**

```java
class Parent {
    protected void method() { }
}

class Child extends Parent {
    public void method() { }        // ✅ More accessible (protected → public)
    // private void method() { }    // ❌ Less accessible
}
```

### 3️⃣ **Exception Handling (Same or Narrower)**

```java
class Parent {
    public void greet() throws IOException { }
    public void sayHello() { }
}

class Child extends Parent {
    public void greet() throws FileNotFoundException { }  // ✅ Narrower exception
    public void sayHello() throws IOException { }         // ❌ New broader exception
}
```

**FileNotFoundException** is a subclass of **IOException** ✅ **IOException** is broader than no exception ❌

### 4️⃣ **Covariant Return Types**

```java
class Item {
    protected Number calculatePrice(float price) {       // Returns Number
        return price + price * 0.2;
    }
}

class Shoe extends Item {
    @Override
    public Double calculatePrice(float shoePrice) {      // Returns Double
        return (shoePrice + shoePrice * 0.2) * 1.05;
    }
}
```

**Double** is a subtype of **Number** ✅

---

## 🚫 Private and Static Methods

### 🔒 Private Methods - No Overriding

```java
class Parent {
    private void secret() { }       // Not visible to subclasses
}

class Child extends Parent {
    private void secret() { }       // ✅ Different method, not overriding
    // @Override                    // ❌ Would cause compilation error
}
```

### 🏠 Static Methods - Method Hiding

```java
class A {
    public static void greet() {
        System.out.println("Hello.");
    }
}

class B extends A {
    public static void greet() {           // Method hiding, not overriding
        System.out.println("Good afternoon.");
    }
    // @Override                           // ❌ Would cause compilation error
}

A.greet();    // Output: "Hello."
B.greet();    // Output: "Good afternoon."
```

**Key Differences:**

- **🔒 Private methods** - Cannot be overridden (not inherited)
- **🏠 Static methods** - "Hidden" rather than overridden
- **🔐 Final methods** - Cannot be overridden or hidden

---

## 📊 Variable Hiding vs Method Overriding

**Variables are hidden, NOT overridden:**

```java
class Mammal {
    public String name = "Unknown";
}

class Dog extends Mammal {
    public String name = "Rex";           // Hides parent variable
    
    public static void main(String[] args) {
        Dog d = new Dog();
        Mammal m = d;                     // Same object, different reference type
        
        System.out.println(d.name);      // "Rex" - Dog reference
        System.out.println(m.name);      // "Unknown" - Mammal reference
    }
}
```

**Key Difference:**

- **🔄 Methods** - Overriding uses runtime object type
- **📊 Variables** - Hiding uses compile-time reference type

---

## 🎯 Summary Table

|Feature|Overriding|Hiding|Notes|
|---|---|---|---|
|**Instance Methods**|✅|❌|Uses runtime object type|
|**Static Methods**|❌|✅|Uses compile-time reference type|
|**Variables**|❌|✅|Uses compile-time reference type|
|**Private Members**|❌|❌|Not inherited|
|**Final Methods**|❌|❌|Cannot be changed|

---

## 💡 Key Takeaways

- **🎭 Polymorphism** - Overriding enables objects to behave differently based on their actual type
- **📝 @Override** - Always use this annotation to catch mistakes
- **🔼 super** - Access parent implementation when extending behavior
- **📋 Rules matter** - Signature, access level, exceptions, and return types have specific requirements
- **🏠 Static/Private** - These are hidden, not overridden
- **📊 Variables** - Always hidden based on reference type, never overridden

---