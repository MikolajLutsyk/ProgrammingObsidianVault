# ☕ Java [[String]] [[Defining Methods|Methods]]


**Tags:** #java #string #methods #oca

Java strings provide a rich set of methods for manipulation, comparison, and formatting. Understanding these methods is essential for effective string handling in Java.

---

## 🔹 Core Concepts

### 🔗 Method Chaining

```java
String result = "Hello World".toLowerCase().replace("world", "java");
```

**How it works:** String methods can be "chained" together, performing operations from left to right in a single statement.

### 🔒 Immutability

```java
String original = "Hello";
String modified = original.toUpperCase(); // Returns new String
// original is still "Hello"
```

**Key Point:** Strings in Java are immutable - methods return new String objects rather than modifying the original.

---

## 📏 String Information Methods

### 📊 Length

```java
String str = "Hello World";
int length = str.length();
System.out.println(length); // Outputs 11
```

### 🔍 Index Of

```java
String str = "Hello World";
int index = str.indexOf('o');
System.out.println(index); // Outputs 4
```

**Returns:** Index of first occurrence, or -1 if not found.

### ✂️ Substring

```java
String str = "Hello, World!";
String sub = str.substring(7, 12);
System.out.println(sub); // Outputs "World"
```

---

## 🔄 Case Conversion

### 🔤 To Lower Case

```java
String str = "Hello World";
String lower = str.toLowerCase();
System.out.println(lower); // Outputs "hello world"
```

### 🔠 To Upper Case

```java
String str = "Hello World";
String upper = str.toUpperCase();
System.out.println(upper); // Outputs "HELLO WORLD"
```

---

## ⚖️ String Comparison Methods

### 🎯 Equals (Case Sensitive)

```java
String str1 = "Hello";
String str2 = "Hello";
String str3 = "hello";
System.out.println(str1.equals(str2)); // Outputs true
System.out.println(str1.equals(str3)); // Outputs false
```

### 🎯 Equals Ignore Case

```java
String str1 = "Hello";
String str2 = "hello";
System.out.println(str1.equalsIgnoreCase(str2)); // Outputs true
```

### 🔚 Ends With

```java
String str = "Hello World";
boolean endsWith = str.endsWith("World");
System.out.println(endsWith); // Outputs true
```

### 🔛 Starts With

```java
String str = "Hello World";
boolean startsWith = str.startsWith("Hello");
System.out.println(startsWith); // Outputs true
```

### 📦 Contains

```java
String str = "Hello World";
boolean contains = str.contains("o W");
System.out.println(contains); // Outputs true
```

---

## 🔧 Modification and Formatting

### 🔄 Replace

```java
String str = "Hello World";
String replaced = str.replace('o', 'a');
System.out.println(replaced); // Outputs "Hella Warld"
```

### ✨ Strip and Trim

```java
String str = "  Hello World  ";
System.out.println(str.strip()); // Outputs "Hello World"
System.out.println(str.trim()); // Outputs "Hello World"
```

**Difference:** `strip()` is Unicode-aware (Java 11+), while `trim()` only removes characters ≤ U+0020.

### 🎯 Strip Leading/Trailing

```java
String str = "  Hello World  ";
System.out.println(str.stripLeading()); // Outputs "Hello World  "
System.out.println(str.stripTrailing()); // Outputs "  Hello World"
```

**Since:** Java 11 - Unicode-aware whitespace removal.

### 📐 Indent

```java
String str = "Hello\nWorld";
String indented = str.indent(2);
System.out.println(indented);
// Outputs:
//   Hello
//   World
```

**Since:** Java 12 - Positive values add spaces, negative values remove them.

### 📝 Strip Indent

```java
String str = "  Hello\n    World";
String stripped = str.stripIndent();
System.out.println(stripped);
// Outputs:
// Hello
//   World
```

**Since:** Java 12 - Removes incidental leading whitespace from multiline strings.

### 🔤 Translate Escapes

```java
String str = "Hello\\tWorld";
String translated = str.translateEscapes();
System.out.println(translated); // Outputs "Hello	World"
```

**Purpose:** Converts escape sequences like `\t`, `\n` into their actual characters.

---

## ✅ State Checking

### 🕳️ Is Empty vs Is Blank

```java
String emptyStr = "";
String blankStr = "   ";
System.out.println(emptyStr.isEmpty()); // Outputs true
System.out.println(blankStr.isEmpty()); // Outputs false
System.out.println(emptyStr.isBlank()); // Outputs true
System.out.println(blankStr.isBlank()); // Outputs true
```

**Difference:** `isEmpty()` checks length = 0, `isBlank()` checks for empty or whitespace-only (Java 11+).

---

## 🎨 String Formatting

### 📋 Format Methods

```java
String name = "World";
int year = 2025;

// Using format()
String formattedStr1 = String.format("Hello, %s! The year is %d.", name, year);
System.out.println(formattedStr1); // Outputs "Hello, World! The year is 2025."

// Using formatted()
String template = "Hello, %s! The year is %d.";
String formattedStr2 = template.formatted(name, year);
System.out.println(formattedStr2); // Outputs "Hello, World! The year is 2025."
```

**Available Since:** `format()` - Java 5, `formatted()` - Java 15

---