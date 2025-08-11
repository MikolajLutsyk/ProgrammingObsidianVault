# ⚠️ Java Exceptions Overview

**Tags:** #java #exceptions #error-handling #runtime #oca

Exceptions occur when something goes wrong during runtime execution.

---

## 🎯 What Are Exceptions?

**Exceptions** occur when something goes wrong during runtime:

- **➗ Division by zero** - Mathematical error
- **📊 [[Arrays|Array]] index out of bounds** - Accessing non-existent array element
- **🚫 Null reference** - Using null as a reference
- **📝 Invalid method parameters** - Passing disallowed values
- **📁 File not found** - Accessing non-existent file
- **🗄️ Database connection** - Unable to connect to database

---

## 🏗️ Exception Hierarchy

```java
java.lang.Throwable
├── java.lang.Exception (checked)
│   └── java.lang.RuntimeException (unchecked)
└── java.lang.Error (unchecked)
```

### 🔍 Exception Categories:

|Type|Checked/Unchecked|Must Handle?|Examples|
|---|---|---|---|
|**⚠️ Error**|Unchecked|Optional|OutOfMemoryError|
|**🔧 RuntimeException**|Unchecked|Optional|NullPointerException|
|**📋 Other Exceptions**|Checked|Required|IOException|

---

## ✅ Checked vs Unchecked

### ✅ **Checked Exceptions**

- **📝 Must be declared or handled** by application code
- **📋 Inherit Exception** but not RuntimeException
- **🔧 Compile-time requirement** - Code won't compile without handling

### ❌ **Unchecked Exceptions**

- **🔧 RuntimeException and Error** subclasses
- **🔄 Optional handling** - May or may not be handled
- **⚡ Runtime occurrence** - Happen during execution

---

## 🔧 Exception Handling Methods

### 🎯 **Method 1: Declare with `throws`**

```java
void readFile(File fileName) throws IOException {
    // Method that might throw IOException
}
```

### 🛡️ **Method 2: Handle with `try-catch`**

```java
void readFile(File fileName) {
    try {
        // Code that might throw exception
    } catch (IOException e) {
        // Handle the exception
    }
}
```

### ⚡ **Method 3: Throw Manually**

```java
if (condition) {
    throw new IllegalArgumentException();
}
```

---

## 🎯 Key Takeaways

- **⚠️ Runtime Problems** - Exceptions represent runtime errors
- **🏗️ Hierarchy Structure** - All inherit from Throwable
- **✅ Checked Required** - Must handle checked exceptions at compile-time
- **❌ Unchecked Optional** - Runtime exceptions can be handled optionally
- **🔧 Two Approaches** - Declare with throws OR handle with try-catch
- **⚡ Manual Throwing** - Can throw exceptions programmatically

---