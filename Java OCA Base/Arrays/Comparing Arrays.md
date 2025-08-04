# ⚖️ Java [[Arrays]].compare()

**Tags:** #java #arrays #compare #methods #oca 

`Arrays.compare()` determines which array is "smaller" by performing lexicographic comparison and returns an integer indicating their relative order.

---

## 🔹 Return Values

### 📊 Comparison Results

```java
import java.util.Arrays;

int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 4};
int result = Arrays.compare(arr1, arr2);
```

**Return Values:**

- **Negative number** - first array is smaller than second
- **Zero** - arrays are equal in content
- **Positive number** - first array is larger than second

---

## 📏 What Makes an Array "Smaller"?

### 📉 Length Comparison

```java
int[] shorter = {1, 2};
int[] longer = {1, 2, 3};
System.out.println(Arrays.compare(shorter, longer)); // Negative (shorter < longer)
```

**Rule 1:** If one array has fewer elements, it's considered smaller.

### 🔍 Element-by-Element Comparison

```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 4};
System.out.println(Arrays.compare(arr1, arr2)); // Negative (3 < 4)
```

**Rule 2:** If arrays have the same length, the one with the first different smaller element is smaller.

### 🕳️ Null Handling

```java
Integer[] arr1 = {null, 2, 3};
Integer[] arr2 = {1, 2, 3};
System.out.println(Arrays.compare(arr1, arr2)); // Negative (null < 1)
```

**Rule 3:** `null` is considered smaller than any other value.

---

## 🔤 [[String]] Comparison Rules

### 🏷️ Prefix Comparison

```java
String[] arr1 = {"cat"};
String[] arr2 = {"category"};
System.out.println(Arrays.compare(arr1, arr2)); // Negative ("cat" is prefix of "category")
```

**Rule:** One string is smaller if it's a prefix of another.

### 🔢 Numbers vs Letters

```java
String[] arr1 = {"123"};
String[] arr2 = {"abc"};
System.out.println(Arrays.compare(arr1, arr2)); // Negative (numbers < letters)
```

**Rule:** Numbers come before letters in comparison order.

### 📝 Case Sensitivity

```java
String[] arr1 = {"Apple"};
String[] arr2 = {"apple"};
System.out.println(Arrays.compare(arr1, arr2)); // Negative (uppercase < lowercase)
```

**Rule:** Uppercase letters are smaller than lowercase letters.

### 🔤 Alphabetical Order

```java
String[] arr1 = {"apple"};
String[] arr2 = {"banana"};
System.out.println(Arrays.compare(arr1, arr2)); // Negative ("apple" < "banana")
```

**Rule:** Standard alphabetical ordering is applied.

---

## 💡 Practical Examples

### 🎯 Complete Comparison Examples

```java
import java.util.Arrays;

// Length difference
int[] short1 = {1, 2};
int[] long1 = {1, 2, 3};
System.out.println(Arrays.compare(short1, long1)); // Negative

// Content difference
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 4};
System.out.println(Arrays.compare(arr1, arr2)); // Negative

// Equal arrays
int[] equal1 = {1, 2, 3};
int[] equal2 = {1, 2, 3};
System.out.println(Arrays.compare(equal1, equal2)); // 0

// String comparison
String[] fruits1 = {"apple", "banana"};
String[] fruits2 = {"apple", "cherry"};
System.out.println(Arrays.compare(fruits1, fruits2)); // Negative ("banana" < "cherry")
```

---