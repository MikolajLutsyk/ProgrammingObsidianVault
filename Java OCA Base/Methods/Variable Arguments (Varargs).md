# 📦 Java Variable Arguments (Varargs)

**Tags:** #java #varargs #oca

Varargs allow a method to accept any number of parameters of the same type using the `...` syntax.

---

## 🔹 Varargs Rules

### 📝 Two Critical Rules

1. **At most one varargs** parameter per [[Defining Methods|methods]]
2. **Varargs must be last** parameter in the list

```java
// ✅ Valid
public void greet(String greeting, String... names) {}

// ❌ Invalid - varargs not last
public void process(String... items, int count) {} // DOES NOT COMPILE

// ❌ Invalid - multiple varargs  
public void mix(String... names, int... numbers) {} // DOES NOT COMPILE
```

---

## 🎯 Basic Usage

### 🗣️ Simple Example

```java
public void greet(String greeting, String... names) {
    for (String name : names) {
        System.out.println(greeting + ", " + name + "!");
    }
}

// Usage
greet("Hello", "John", "George", "Luke");
```

**Output:**

```
Hello, John!
Hello, George!
Hello, Luke!
```

---

## 📋 Array vs Varargs

### ✅ Valid Array Passing

```java
String[] allNames = {"Peter", "Paul"};
greet("Hello", allNames);  // Pass existing array
```

**Output:**

```
Hello, Peter!
Hello, Paul!
```

### ❌ Anonymous Array Issues

```java
// ❌ Anonymous array literal - DOES NOT COMPILE
greet("Hello", {"John", "George", "Luke"});

// ✅ Explicit array creation - OK
greet("Hello", new String[]{"John", "George", "Luke"});
```

---

## 🚀 Main Method with Varargs

### 📱 Alternative Main Signature

```java
public static void main(String... args) {
    // Works the same as String[] args
}
```

**Flexibility:** Can use varargs syntax in main method declaration.

---

## 💡 Key Points

### 🔄 Behind the Scenes

- Varargs are **arrays** internally
- Compiler converts varargs calls to array creation
- Can pass 0, 1, or many arguments

### 🎨 Usage Examples

```java
greet("Hi");                    // 0 names
greet("Hi", "Alice");          // 1 name  
greet("Hi", "Bob", "Carol");   // 2 names
```

---