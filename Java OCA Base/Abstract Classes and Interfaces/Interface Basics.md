# 🔌 Java Interfaces Basics

**Tags:** #java #interface #oop #oca

Interfaces provide a way to achieve multiple [[Inheritance]] in Java when a class needs to "extend" more than one [[Abstract Classes|abstract class]].

---

## 🎯 What Are Interfaces?

A [[Class Basics|class]] can only extend one class, but can **implement any number of interfaces** using the `implements` keyword.

```java
public interface Car {
    int distanceWithFullTank(int tankVolume);
    int MAXIMUM_WEIGHT = 2000;
}

public interface Ford {
    String getColor();
}

public class FordModelT implements Car, Ford {
    public int distanceWithFullTank(int tankVolume) {
        return tankVolume * 9;
    }
    
    public String getColor() {
        return "black";
    }
}
```

**Key Points:**

- Similar to abstract classes
- Cannot create instance using `new` keyword
- Use `implements` keyword, separated by commas

---

## 🔍 Implicit Keywords

```java
// What you write:
public interface Car {
    int distanceWithFullTank(int tankVolume);    // Abstract method (no body)
    int MAXIMUM_WEIGHT = 2000;                   // Constant field
}

// What Java sees (implicit keywords):
public abstract interface Car {
    public abstract int distanceWithFullTank(int tankVolume);
    public static final int MAXIMUM_WEIGHT = 2000;
}
```

**Important:** All interfaces are implicitly abstract, so they cannot be marked as `final`.

---

## 📋 Rules of Implementation

1. **`public` keyword is required**
2. **Return type must be covariant** with the interface [[Defining Methods|method]]
3. **Signature** (name & parameters) must match the interface method
4. **All inherited methods must be implemented** (overriding rules apply)

---

## 🔗 Interface Inheritance

An interface can extend another interface:

```java
public interface Mammal {
    public int eats();
}

public interface CanSwim extends Mammal {
    public int swim();
}

public class Elephant implements CanSwim {
    public int swim() { return 5; }
    public int eats() { return -1; }    // Must implement both swim() and eats()
}
```

---

## ⚖️ Duplicate Methods

### ✅ Example #1 - Compatible Return Types

```java
public interface Tetrapod {
    public void eats();
}

public interface Mammal {
    public void eats();
}

public class Dog implements Tetrapod, Mammal {
    public void eats() {
        System.out.println("Dog is eating.");
    }
}
```

**This is OK** because the return types match (covariant or same).

### ❌ Example #2 - Incompatible Return Types

```java
public interface Tetrapod {
    public void eats();
}

public interface Mammal {
    public int eats();
}

public class Dog implements Tetrapod, Mammal {
    public void eats() {
        System.out.println("Dog is eating.");
    }
}
```

**This does not compile** (non-covariant return types). Another way to think about this is that `int eats()` is not implemented.

---