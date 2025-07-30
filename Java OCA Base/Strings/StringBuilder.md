# 🛠️ Java StringBuilder

**Tags:** #java #stringbuilder #mutable #strings

StringBuilder is a mutable class designed for efficient string manipulation. Unlike immutable String objects, StringBuilder allows you to modify the content without creating new objects.

---

## 🔹 Core Concept

### 🔄 Mutable [[String]] Container

```java
StringBuilder name = new StringBuilder("John Wayne");
// Can be modified in-place without creating new objects
```

**Key Advantage:** Efficient for multiple string operations - no new object creation for each modification.

---

## 📏 Inherited String-like Methods

### 📊 Length

```java
StringBuilder sb = new StringBuilder("Hello World");
int length = sb.length(); // Returns 11
```

### 🔍 Index Of

```java
StringBuilder sb = new StringBuilder("Hello World");
int index = sb.indexOf("o"); // Returns 4
```

### 📍 Character At

```java
StringBuilder sb = new StringBuilder("Hello");
char ch = sb.charAt(1); // Returns 'e'
```

### ✂️ Substring

```java
StringBuilder sb = new StringBuilder("Hello World");
String sub = sb.substring(6, 11); // Returns "World"
// Note: Returns String, does NOT modify the StringBuilder
```

---

## 🔧 Modification Methods

### ➕ Append

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World"); // sb becomes "Hello World"
sb.append('!');      // sb becomes "Hello World!"
```

### 📥 Insert

```java
StringBuilder sb = new StringBuilder("Hello World");
sb.insert(6, "Beautiful "); // sb becomes "Hello Beautiful World"
```

### ❌ Delete

```java
StringBuilder sb = new StringBuilder("Hello Beautiful World");
sb.delete(6, 16); // sb becomes "Hello World" (removes "Beautiful ")
```

### 🗑️ Delete Character At

```java
StringBuilder sb = new StringBuilder("Hello!");
sb.deleteCharAt(5); // sb becomes "Hello" (removes '!')
```

### 🔄 Replace

```java
StringBuilder sb = new StringBuilder("Hello World");
sb.replace(6, 11, "Java"); // sb becomes "Hello Java"
sb.replace(6, 999, "Everyone"); // sb becomes "Hello Everyone" (end index too large)
```

**Note:** If final index exceeds length, replace goes through the end of the string.

### 🔀 Reverse

```java
StringBuilder sb = new StringBuilder("Hello");
sb.reverse(); // sb becomes "olleH"
```

### 🔤 To String

```java
StringBuilder sb = new StringBuilder("Hello World");
String result = sb.toString(); // Converts to immutable String
```

---

## ⚠️ Important Differences

### 🚫 No Equals Method

```java
StringBuilder sb1 = new StringBuilder("Hello");
StringBuilder sb2 = new StringBuilder("Hello");
System.out.println(sb1.equals(sb2)); // Returns false (same as ==)
System.out.println(sb1 == sb2);      // Returns false
```

**Warning:** StringBuilder does not override `equals()` - it uses reference equality like `==`.

### 📤 Substring Behavior

```java
StringBuilder sb = new StringBuilder("Hello World");
String sub = sb.substring(0, 5); // Returns "Hello" as String
System.out.println(sb.toString()); // Still "Hello World" - unchanged!
```

**Key Point:** `substring()` returns a String and does NOT modify the original StringBuilder.

---