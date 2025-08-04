# 🔀 Java [[Arrays]].sort() Reference

**Tags:** #java #arrays #sort #sorting #mutable #oca

`Arrays.sort()` arranges array elements in ascending order. It modifies the original array in-place, making it a mutating operation.

---

## 🔹 Basic Usage

### 📊 Sorting an Array

```java
import java.util.Arrays;

int[] nums = new int[] {3, -1, 17};
Arrays.sort(nums);
System.out.println(Arrays.toString(nums)); // Outputs: [-1, 3, 17]
```

**Key Points:**

- **In-place sorting** - modifies the original array
- **Ascending order** - smallest to largest
- **No return value** - `void` method

---

## ⚠️ Mutable Behavior

### 🔄 Original Array Modified

```java
int[] original = {5, 2, 8, 1};
System.out.println("Before: " + Arrays.toString(original)); // [5, 2, 8, 1]

Arrays.sort(original);
System.out.println("After: " + Arrays.toString(original));  // [1, 2, 5, 8]
```

**Important:** Arrays are mutable - `sort()` changes the original array permanently.

### 💾 No New Array Created

```java
int[] nums = {3, -1, 17};
int[] reference = nums;  // Same array reference

Arrays.sort(nums);
System.out.println(Arrays.toString(nums));      // [-1, 3, 17]
System.out.println(Arrays.toString(reference)); // [-1, 3, 17] - also changed!
```

**Behavior:** Both variables point to the same modified array.

---

## 🎯 Different Data Types

### 🔢 Integer Arrays

```java
int[] numbers = {42, 7, 23, 1, 56};
Arrays.sort(numbers);
System.out.println(Arrays.toString(numbers)); // [1, 7, 23, 42, 56]
```

### 🔤 [[String]] Arrays

```java
String[] words = {"banana", "apple", "cherry", "date"};
Arrays.sort(words);
System.out.println(Arrays.toString(words)); // [apple, banana, cherry, date]
```

### 💰 Double Arrays

```java
double[] prices = {19.99, 5.50, 12.75, 3.25};
Arrays.sort(prices);
System.out.println(Arrays.toString(prices)); // [3.25, 5.5, 12.75, 19.99]
```

---

## 📋 Practical Examples

### 🔄 Before and After Comparison

```java
import java.util.Arrays;

// Example 1: Mixed positive and negative numbers
int[] mixedNums = {10, -5, 0, 3, -12, 7};
System.out.println("Original: " + Arrays.toString(mixedNums));
Arrays.sort(mixedNums);
System.out.println("Sorted:   " + Arrays.toString(mixedNums));
// Output: [-12, -5, 0, 3, 7, 10]

// Example 2: Already sorted array
int[] alreadySorted = {1, 2, 3, 4, 5};
Arrays.sort(alreadySorted);  // Still works, no change needed
System.out.println("Still sorted: " + Arrays.toString(alreadySorted));
// Output: [1, 2, 3, 4, 5]

// Example 3: Reverse order
int[] reversed = {9, 7, 5, 3, 1};
Arrays.sort(reversed);
System.out.println("Now ascending: " + Arrays.toString(reversed));
// Output: [1, 3, 5, 7, 9]
```

---

## 💡 Usage Tips

### 🎯 Common Pattern with Binary Search

```java
int[] data = {17, 3, -1, 9, 12};

// Step 1: Sort for binary search
Arrays.sort(data);  // [-1, 3, 9, 12, 17]

// Step 2: Now binary search works correctly
int index = Arrays.binarySearch(data, 9);
System.out.println("Found 9 at index: " + index); // Found 9 at index: 2
```

### 🔒 Preserving Original Array

```java
int[] original = {5, 2, 8, 1};
int[] copy = original.clone();  // Create copy first

Arrays.sort(copy);  // Sort the copy, not the original
System.out.println("Original: " + Arrays.toString(original)); // [5, 2, 8, 1]
System.out.println("Sorted:   " + Arrays.toString(copy));     // [1, 2, 5, 8]
```

---