# 🗂️ Java [[Arrays]] Declaration & Initialization

**Tags:** #java #array #declaration #initialization

Arrays in Java can be declared and initialized in various ways. Understanding the syntax and different approaches is essential for effective array usage.

---

## 🔹 Declaring an Array

### 📝 Basic Declaration Syntax

```java
int[] nums = new int[3];
```

**Key Elements:**

- **`[]`** - indicates "array" type
- **`nums`** - variable name
- **`new`** - keyword for object creation
- **`3`** - size of the array

---

## 🔧 Initializing an Array

### 🎯 Declare First, Initialize Later

```java
int[] nums = new int[3];  // Declaration with size
nums[0] = 3;              // Manual initialization
nums[1] = -1;
nums[2] = 17;
```

### ⚡ Quick Initialization (Without `new`)

```java
int[] nums = new int[3];
nums = {3, -1, 17};  // ERROR: This syntax only works during declaration
```

**Note:** This shorthand syntax is NOT allowed for existing arrays.

### 🔄 Declaration & Initialization Combined

```java
// With explicit new keyword
int[] myNumbers = new int[]{3, -1, 17};

// Shorthand syntax (preferred)
int[] myNumbers = {3, -1, 17};
```

---

## 📐 Declaration Syntax Variations

### ✅ Allowed Declaration Styles

```java
int[] nums;     // Standard style (recommended)
int [] nums;    // Space after type
int []nums;     // Space before variable
int nums[];     // C-style declaration
int nums [];    // C-style with space
```

### ❌ Invalid Declaration

```java
int[3] nums = ...;  // DOES NOT COMPILE
```

**Rule:** Size can only be specified on the right-hand side during initialization.

---

## 🔗 Multiple Declarations

### 📊 Multiple Arrays

```java
int[] myNumbers, myIntValues;  // Both are int arrays
```

### 🎭 Mixed Declaration

```java
int myNumbers[], a;  // myNumbers is int[], a is int
```

**Important:** Only the first variable gets the array brackets in this style.

---

## ⚠️ Important Array Behaviors

### 🚫 No Equals Method

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 3};
System.out.println(arr1.equals(arr2)); // false - compares references
System.out.println(arr1 == arr2);      // false - different objects
```

**Warning:** Arrays don't override `equals()` - use `Arrays.equals()` for content comparison.

### 🖨️ Printing Arrays

```java
import java.util.Arrays;

int[] numbers = {3, -1, 17};

// Wrong way - prints memory reference
System.out.println(numbers); // Outputs: [I@hashcode

// Correct way - prints array content
System.out.println(Arrays.toString(numbers)); // Outputs: [3, -1, 17]
```

### 📏 Array Length

```java
int[] scores = {85, 92, 78, 96, 88};
System.out.println(scores.length); // Outputs: 5
```

**Note:** `length` is a property (not a method) - no parentheses needed.

---
