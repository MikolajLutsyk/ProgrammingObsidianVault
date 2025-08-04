# 🔍 Java [[Arrays]].binarySearch() Reference

**Tags:** #java #arrays #binarySearch #search #sorted #oca

`Arrays.binarySearch()` efficiently finds elements in sorted arrays using binary search algorithm. It requires the array to be sorted for predictable results.

---

## ⚠️ Critical Requirements

### 📊 Sorted Arrays Only

```java
int[] sorted = {-1, 3, 17};     // ✅ Sorted - predictable results
int[] unsorted = {3, -1, 17};   // ❌ Unsorted - unpredictable results
```

**Warning:** Binary search only works correctly on sorted arrays. Unsorted arrays produce unpredictable results.

---

## 🔹 Method Signature

### 📝 Basic Usage

```java
Arrays.binarySearch(array, targetElement)
```

**Parameters:**

- **`array`** - the sorted array to search in
- **`targetElement`** - the element to find

---

## 📊 Return Values

### ✅ Element Found

```java
int[] nums = {-1, 3, 17};  // Already sorted
System.out.println(Arrays.binarySearch(nums, -1)); // Returns: 0
System.out.println(Arrays.binarySearch(nums, 3));  // Returns: 1
System.out.println(Arrays.binarySearch(nums, 17)); // Returns: 2
```

**Behavior:** Returns the actual index of the found element (zero-based).

### ❌ Element Not Found

```java
int[] nums = {-1, 3, 17};  // Sorted array
System.out.println(Arrays.binarySearch(nums, 0));  // Returns: -2
System.out.println(Arrays.binarySearch(nums, 10)); // Returns: -3
System.out.println(Arrays.binarySearch(nums, -5)); // Returns: -1
```

**Formula:** Returns `-(insertion_point + 1)` where insertion_point is where the element would belong.

---

## 🧮 Understanding Negative Results

### 📍 Insertion Point Logic

```java
int[] nums = {-1, 3, 17};
// Array positions: [0] [1] [2]
//                  -1   3  17

int result = Arrays.binarySearch(nums, 0);
System.out.println(result); // Returns: -2
```

**Explanation:**

- `0` would belong at index 1 (between -1 and 3)
- Formula: `-(1 + 1) = -2`
- **Think:** "0 would be at the 2nd place (index 1) in the array"

### 🎯 More Examples

```java
int[] nums = {-1, 3, 17};

// Element -5 would go at index 0 (before -1)
System.out.println(Arrays.binarySearch(nums, -5)); // Returns: -1
// Formula: -(0 + 1) = -1

// Element 10 would go at index 2 (between 3 and 17)  
System.out.println(Arrays.binarySearch(nums, 10)); // Returns: -3
// Formula: -(2 + 1) = -3

// Element 20 would go at index 3 (after 17)
System.out.println(Arrays.binarySearch(nums, 20)); // Returns: -4
// Formula: -(3 + 1) = -4
```

---

## 🚨 Unsorted Array Behavior

### ⚡ Unpredictable Results

```java
int[] myNums = {3, -1, 17};  // Unsorted!
System.out.println(Arrays.binarySearch(myNums, -1)); 
// Returns: unpredictable result (could be any value)
```

**Problem:** Binary search assumes sorted data. Unsorted arrays break the algorithm's assumptions.

### ✅ Correct Approach

```java
int[] myNums = {3, -1, 17};
Arrays.sort(myNums);         // Sort first: [-1, 3, 17]
System.out.println(Arrays.binarySearch(myNums, -1)); 
// Returns: 0 (predictable, correct result)
```

---

## 💡 Practical Example

### 🔄 Complete Workflow

```java
import java.util.Arrays;

int[] numbers = {3, -1, 17, 5, 9};

// Step 1: Sort the array
Arrays.sort(numbers);  // Result: [-1, 3, 5, 9, 17]
System.out.println("Sorted: " + Arrays.toString(numbers));

// Step 2: Search for existing elements
System.out.println("Search for 5: " + Arrays.binarySearch(numbers, 5));   // Returns: 2
System.out.println("Search for -1: " + Arrays.binarySearch(numbers, -1)); // Returns: 0

// Step 3: Search for non-existing elements
System.out.println("Search for 0: " + Arrays.binarySearch(numbers, 0));   // Returns: -2
System.out.println("Search for 7: " + Arrays.binarySearch(numbers, 7));   // Returns: -4
System.out.println("Search for 20: " + Arrays.binarySearch(numbers, 20)); // Returns: -6
```

---