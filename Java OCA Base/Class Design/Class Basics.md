# 🏗️ Java Class Basics

**Tags:** #java #class #oop #object-oriented

A **class** is a blueprint or template for creating objects in Java. It defines the structure and behavior that objects of that class will have.

---

## 🎯 What is a Class?

A class contains:

- **📦 Fields (Variables)** - Store data/state
- **⚙️ Methods** - Define behavior/actions
- **🔧 Constructors** - Initialize new objects

```java
public class Dog {
    // Fields (data)
    private String name;
    private int age;
    
    // Constructor
    public Dog(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // Methods (behavior)
    public void bark() {
        System.out.println(name + " says Woof!");
    }
    
    public int getAge() {
        return age;
    }
}
```

---

## 🔍 Key Points

- **🏭 Blueprint**: Class defines what objects will look like
- **🎪 Objects**: Created from classes using `new` keyword
- **📝 Naming**: Class names should be PascalCase (e.g., `MyClass`)
- **📁 File**: Each public class must be in its own `.java` file

### 💡 Example Usage

```java
Dog myDog = new Dog("Buddy", 3);  // Create object from class
myDog.bark();                     // Use object's method
// Output: Buddy says Woof!
```

---