# 🔲 Java Multidimensional [[Arrays]]

**Tags:** #java #array #multidimensional #oca

Multidimensional arrays in Java are arrays of arrays, allowing you to store data in a table-like structure with rows and columns.

---

## 🔹 Declaration & Initialization

### 📊 Array of Arrays

```java
int[][] a = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};
```

**Structure:** Each row can have different lengths (jagged arrays).

**Visual Layout:**

```
Row 0: [-1, 17]
Row 1: [3]
Row 2: [5, 103, 11]
Row 3: [4, 9, -6, 8]
```

---

## 🔄 Accessing Elements

### 🎯 Traditional For Loop

```java
int[][] a = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};

for (int i = 0; i < a.length; i++)
    for (int j = 0; j < a[i].length; j++)
        System.out.println("a(%d, %d) = %d".formatted(i, j, a[i][j]));
```

**Output:**

```
a(0, 0) = -1    a(0, 1) = 17
a(1, 0) = 3
a(2, 0) = 5     a(2, 1) = 103   a(2, 2) = 11
a(3, 0) = 4     a(3, 1) = 9     a(3, 2) = -6    a(3, 3) = 8
```

**Advantage:** Full control over row and column indices.

### 🔁 For-Each Loop

```java
int[][] a = {{-1, 17}, {3}, {5, 103, 11}, {4, 9, -6, 8}};

for (int[] row : a)
    for (int element : row)
        System.out.println("element = " + element);
```

**Behavior:** Iterates through all elements without index information.

---