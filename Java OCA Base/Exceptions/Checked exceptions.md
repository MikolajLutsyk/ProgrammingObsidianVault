# ✅ Java Checked [[Exceptions]]

**Tags:** #java #checked-exceptions #oca

Checked exceptions must be declared or handled by application code where they are thrown.

---

## 🎯 What Are Checked Exceptions?

**Checked Exceptions** have mandatory handling requirements:

- **📝 Must be declared or handled** by application code
- **📋 Inherit Exception** but not RuntimeException
- **🔧 Compile-time requirement** - Code won't compile without proper handling

---

## ❌ Problem Example - Won't Compile

```java
void readFirstByteFromFile(File fileName) {
    FileInputStream file = new FileInputStream(fileName);  // IOException possible
    byte x = (byte) file.read();                          // IOException possible
    System.out.println(x);
}
// ❌ DOES NOT COMPILE - IOException not handled
```

---

## 🔧 Fix #1 - Declare with `throws`

```java
void readFirstByteFromFile(File fileName) throws IOException {
    FileInputStream file = new FileInputStream(fileName);
    byte x = (byte) file.read();
    System.out.println(x);
}
// ✅ Compiles, but exception still not handled
```

**🔍 Note:** This compiles but doesn't handle the exception - just passes it up.

---

## 🛡️ Fix #2 - Handle with `try-catch`

```java
void readFirstByteFromFile(File fileName) {
    try {
        FileInputStream file = new FileInputStream(fileName);
        byte x = (byte) file.read();
        System.out.println(x);
    } catch (IOException e) {
        e.printStackTrace();
    }
}
// ✅ Compiles and handles exception - good practice
```

---

## 🏗️ Custom Checked Exceptions

```java
class OutOfMilkException extends Exception {}

public class MyClass {
    private static void getMilk() throws OutOfMilkException {
        System.out.println("Getting the milk...");
    }
    
    public static void main(String args[]) {
        getMilk();  // ❌ DOES NOT COMPILE
    }
}
```

**🔧 Fix:** Main method must also declare or handle:

```java
public static void main(String args[]) throws OutOfMilkException {
    getMilk();  // ✅ OK
}
```

---

## 🎯 Checked Exception Handling Rules

### 📝 **Declaration Rules:**

- **🔧 [[Defining Methods|Method]] signature** - Use `throws` keyword
- **📋 Multiple exceptions** - Separate with commas
- **⬆️ Propagation** - Exception passes to calling method

### 🛡️ **Handling Rules:**

- **🔧 try-catch block** - Surround risky code
- **📋 Specific handling** - Catch specific exception types
- **✅ Good practice** - Handle rather than just declare

---

## 🎯 Key Takeaways

- **✅ Mandatory Handling** - Must declare or handle at compile-time
- **📋 Exception Inheritance** - Extend Exception, not RuntimeException
- **🔧 Two Options** - throws declaration OR try-catch handling
- **🛡️ Better Practice** - Handle exceptions rather than just declare
- **⬆️ Exception Propagation** - throws passes exception to caller
- **🏗️ Custom Exceptions** - Create by [[Inheritance|extending]] Exception [[Class Basics|class]]

---