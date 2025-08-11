# 🛡️ Java [[Exceptions]] Handling Techniques

**Tags:** #java #exception-handling #oca

Advanced techniques for handling multiple exceptions and ensuring cleanup code execution.

---

## 🔧 Multiple Exception Handling

### 📊 **Scenario #1: Subclass and Superclass**

```java
void readFirstByteFromFile(File fileName) {
    try {
        FileInputStream file = new FileInputStream(fileName);
        byte x = (byte) file.read();
        System.out.println(x);
    } catch (FileNotFoundException e) {    // #1 Subclass first
        e.printStackTrace();
    } catch (IOException e) {              // #2 Superclass second
        e.printStackTrace();
    }
}
```

**⚠️ Critical Rule:** Subclass exceptions MUST come before superclass exceptions!

**❌ Wrong Order:**

```java
} catch (IOException e) {              // Superclass first
    e.printStackTrace();
} catch (FileNotFoundException e) {    // ❌ DOES NOT COMPILE - unreachable
    e.printStackTrace();
}
```

---

### 🔄 **Scenario #2: Independent Exceptions (Separate Blocks)**

```java
void readFirstByteFromFile(File fileName) {
    try {
        FileInputStream file = new FileInputStream(fileName);
        byte x = (byte) file.read();
        System.out.println(x);
    } catch (IOException e) {
        e.printStackTrace();
    } catch (NumberFormatException e) {
        e.printStackTrace();
    }
}
```

**✅ OK:** Independent exceptions can be in any order.

---

### 🔗 **Scenario #2A: Independent Exceptions (Multi-Catch)**

```java
void readFirstByteFromFile(File fileName) {
    try {
        FileInputStream file = new FileInputStream(fileName);
        byte x = (byte) file.read();
        System.out.println(x);
    } catch (IOException | NumberFormatException e) {
        e.printStackTrace();
    }
}
```

**🔍 Multi-Catch Rules:**

- **✅ Works only for independent classes** - No [[Inheritance|inheritance]] relationship
- **📝 Single variable name** - Only one exception variable allowed
- **🔗 Pipe separator** - Use `|` to separate exception types

---

## ❌ Incorrect Multi-Catch Syntax

```java
// ❌ Multiple variable names:
catch (IOException e1 | NumberFormatException e2)

// ❌ Same variable name repeated:  
catch (IOException e | NumberFormatException e)
```

---

## 🏁 Finally Block

```java
void readFirstByteFromFile(File fileName) {
    try {
        FileInputStream file = new FileInputStream(fileName);
        byte x = (byte) file.read();
        System.out.println(x);
    } catch (IOException | NumberFormatException e) {
        e.printStackTrace();
    } finally {
        System.out.println("Running readFirstByteFromFile...");
    }
}
```

**🔍 Finally Block Characteristics:**

- **✅ Always executes** - Whether exception is caught or not
- **🧹 Cleanup code** - Perfect for resource cleanup
- **⚡ Guaranteed execution** - Runs even if exception occurs

---

## 📋 Exception Handling Patterns

### 🎯 **Pattern 1: Specific to General**

```java
try {
    // Risky code
} catch (SpecificException e) {
    // Handle specific case
} catch (GeneralException e) {
    // Handle general case
}
```

### 🎯 **Pattern 2: Multiple Independent**

```java
try {
    // Risky code  
} catch (ExceptionA | ExceptionB e) {
    // Handle both the same way
}
```

### 🎯 **Pattern 3: With Cleanup**

```java
try {
    // Risky code
} catch (Exception e) {
    // Handle exception
} finally {
    // Cleanup resources
}
```

---

## ⚠️ Critical Rules Summary

### 🔍 **Catch Block Ordering:**

- **📊 Subclass first** - More specific exceptions before general ones
- **❌ Unreachable catch** - Compiler error if subclass comes after superclass
- **🔄 Independent exceptions** - Any order allowed

### 🔗 **Multi-Catch Syntax:**

- **✅ Independent only** - No inheritance relationship between exceptions
- **📝 Single variable** - Only one exception parameter allowed
- **🔗 Pipe operator** - Use `|` to separate exception types

### 🏁 **Finally Block:**

- **⚡ Always runs** - Executes regardless of exception occurrence
- **🧹 Resource cleanup** - Perfect for closing files, connections, etc.

---

## 🎯 Key Takeaways

- **📊 Order Matters** - Subclass exceptions before superclass exceptions
- **🔗 Multi-Catch** - Use `|` for independent exceptions with same handling
- **❌ Syntax Rules** - Single variable name in multi-catch blocks
- **🏁 Finally Guaranteed** - Finally block always executes
- **🧹 Cleanup Pattern** - Use finally for resource management
- **⚠️ Compile-Time Checks** - Compiler enforces proper exception ordering

---