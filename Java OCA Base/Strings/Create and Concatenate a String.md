# 🔤 Java String Basics

**Tags:** #java #string #oca

[[String]] is a sequence of characters in Java, implementing the `CharSequence` interface. It's one of the most commonly used classes for text manipulation.

---

## 🔹 [[String]] Creation

### 📝 String Declaration

```java
String name = "John Wayne";        // String literal
String name = new String("John Wayne"); // String object
```

**Interface:** Implements `CharSequence` - a sequence of characters with defined ordering.

---

## 🔗 String Concatenation

### ➕ Concatenation Methods

```java
// Using + operator
String result = str1 + str2;

// Using concat() method
String result = str1.concat(str2);
```

### 🎯 Concatenation Rules

#### 🔢 Rule 1: Numeric Addition

```java
int a = 5, b = 3;
System.out.println(a + b); // Outputs: 8 (addition)
```

**When:** Both operands are numeric - `+` performs **addition**.

#### 🔤 Rule 2: String Concatenation

```java
String str = "Hello";
int num = 42;
System.out.println(str + num); // Outputs: "Hello42" (concatenation)
```

**When:** Either operand is a String - `+` performs **concatenation**.

#### ⬅️ Rule 3: Left-to-Right Evaluation

```java
System.out.println(1 + 2 + "Hello"); // Outputs: "3Hello"
System.out.println("Hello" + 1 + 2); // Outputs: "Hello12"
```

**Key Point:** Evaluation proceeds **left to right** - order matters!

---

## 💡 Concatenation Examples

### 🔄 Mixed Operations

```java
int x = 10, y = 20;
String prefix = "Result: ";

System.out.println(x + y + prefix);        // Outputs: "30Result: "
System.out.println(prefix + x + y);        // Outputs: "Result: 1020"
System.out.println(prefix + (x + y));      // Outputs: "Result: 30"
```

### 🎨 Complex Concatenation

```java
String firstName = "John";
String lastName = "Wayne";
int age = 72;

String bio = "Actor " + firstName + " " + lastName + " was " + age + " years old.";
// Outputs: "Actor John Wayne was 72 years old."
```

---