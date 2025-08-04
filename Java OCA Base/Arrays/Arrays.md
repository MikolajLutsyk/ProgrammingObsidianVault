# 🗂️ Array Definition

**Tags:** #java #array #oca

**Array** is a collection of elements of the same data type stored in contiguous memory locations. It's a fundamental data structure in Java that provides indexed access to its elements.

---

## 🔹 Key Characteristics

### 📊 Fixed Size

```java
int[] numbers = new int[5]; // Array of 5 integers
```

**Behavior:** Size is determined at creation time and cannot be changed.

### 🎯 Same Data Type

```java
String[] names = {"John", "Jane", "Bob"}; // All elements are Strings
int[] ages = {25, 30, 35};                // All elements are integers
```

**Requirement:** All elements must be of the same declared type.

### 📍 Indexed Access

```java
int[] scores = {85, 92, 78, 96};
System.out.println(scores[0]); // Outputs: 85 (first element)
System.out.println(scores[3]); // Outputs: 96 (fourth element)
```

**Access:** Elements accessed using zero-based indexing: `array[index]`.

### 💾 Contiguous Memory

```java
int[] data = {10, 20, 30, 40};
// Memory: [10][20][30][40] - stored sequentially
```

**Storage:** Elements stored in adjacent memory locations for efficient access.

---