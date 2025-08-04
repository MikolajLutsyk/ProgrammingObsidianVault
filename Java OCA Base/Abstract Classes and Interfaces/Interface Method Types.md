# 🛠️ Java [[Interface Basics|Interface]] Method Types

**Tags:** #java #interface #default-methods #oop #oca

Interfaces support different types of methods: default, static, and private methods with specific rules and use cases.

---

## 🛠️ Default Interface [[Defining Methods|Methods]]

**Problem:** If you have an interface implemented by 100 classes and need to add another method, making it abstract would require implementing it in all 100 classes.

**Solution:** Default methods are non-abstract and must have a body (default implementation).

```java
public interface Mammal {
    public void walks();
    public void eats();
    
    default void sleeps() {                    // No need to implement in classes
        System.out.println("A mammal sleeps.");
    }
}

public class Dog implements Mammal {
    public void walks() { System.out.println("Dog walks."); }
    public void eats() { System.out.println("Dog eats."); }
    // sleeps() method inherited automatically
}
```

### 📋 Rules for Using Default Methods

1. Keyword `default` can only be used in interfaces
2. Must have a body (default implementation)
3. Implicitly public
4. Cannot be abstract, final, or static
5. May or may not be overridden by implementing classes
6. If class inherits two or more default methods with same signature, it must override the method

### ⚖️ Handling Conflicts

```java
public interface Car {
    public default int getMaxSpeed() { return 100; }
}

public interface Truck {
    default int getMaxSpeed() { return 70; }
}

public class Van implements Car, Truck {
    public int getMaxSpeed() {              // Must override (conflict resolution)
        return 80;
    }
    
    public int getMaxSpeedCar() {
        return Car.super.getMaxSpeed();     // Call specific interface default
    }
}
```

---

## 🏠 Static Interface Methods

```java
public interface Car {
    static int getMaxSpeed() { return 100; }
}

public class Ford implements Car {
    public int getMaxSpeedCar() {
        return Car.getMaxSpeed();           // Access via interface name
    }
}
```

**Important:** Static methods cannot be overridden!

---

## 🔐 Private Interface Methods

```java
public interface Car {
    private static int calculateSpeed() {
        int speed = 70 * 2;
        return speed;
    }
    
    public default int getMaxSpeed() {
        return calculateSpeed();
    }
    
    public default int getRecommendedSpeed() {
        return (int)(calculateSpeed() * 0.8);
    }
}
```

### 📋 Rules for Using Private Interface Methods

1. Marked with keyword `private`
2. Must have a body
3. Private static methods may be called by any method in the interface
4. Non-static private methods may be called only by non-static methods

---

## 🔄 Default and Private Methods Calling Abstract Methods

```java
public interface Car {
    int getMaxSpeed();                      // Abstract methods
    int getHorsePower();
    
    default void printCarFeatures() {
        System.out.println("Max speed: " + getMaxSpeed() + 
                          " | Horse power: " + getHorsePower());
    }
}
```

**Key Point:** These methods are abstract and must be implemented. When you call `printCarFeatures()` from a class that implements the interface, the implementation given in that class will be used in `printCarFeatures()`.

---