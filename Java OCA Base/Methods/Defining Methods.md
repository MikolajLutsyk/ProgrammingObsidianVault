# 🔧 Java Method Syntax

**Tags:** #java #methods #syntax #declaration

Java methods follow a specific syntax structure with required and optional components.

---

## 🔹 Method Syntax Structure

### 📝 Complete Syntax

```java
public final void printName(String name) throws InterruptedException {}
```

**Components:**

- **Access modifier** - `public`, `private`, `protected`
- **Optional specifier** - `static`, `final`, `abstract`
- **Return type** - primitive, object, or `void`
- **Method signature** - name + parameter list
- **Exception (optional)** - `throws` clause
- **Method body** - `{}` block

---

## ❌ Common Syntax Errors

### 🚫 Incorrect Order

```java
public void final printName(); // DOES NOT COMPILE
```

**Rule:** Method signature must follow the return type, not precede it.

### 🔄 Return Type Consistency

```java
// ✅ Correct
public int addNumbers(int a, int b) {
    return a + b;
}

// ❌ Incorrect - type mismatch
public int addNumbers(int a, int b) {
    long c = 1L;
    return c * (a + b); // DOES NOT COMPILE - returns long, not int
}
```

**Rule:** Return value must match declared return type.

---

## 📋 Method Components

### 🏷️ Method Name

```java
public void calculateTotal() {} // Valid identifier
```

**Rule:** Same naming rules as variables (Java identifier).

### 📄 Parameter List

```java
public void processData(String name, int age, boolean active) {}
```

**Rule:** Parameters separated by commas.

### ⚠️ Exception Handling

```java
public void readFile() throws IOException, FileNotFoundException {}
```

**Rule:** Multiple exceptions separated by commas after `throws`.

### 📦 Method Body

```java
public void doNothing() {} // Empty but required
```

**Rule:** Method must have a body `{}`, even if empty.

---

## ✅ Valid Examples

### 🎯 Different Return Types

```java
public int getAge() { return 25; }                    // Primitive
public String getName() { return "John"; }           // Object
public void printInfo() { System.out.println("Hi"); } // Void
```

### 🔧 With Modifiers

```java
public static final String DEFAULT_NAME = "Unknown";
private void validateInput(String input) throws IllegalArgumentException {}
```

---