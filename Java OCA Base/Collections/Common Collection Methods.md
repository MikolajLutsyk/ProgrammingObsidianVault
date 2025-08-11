# 🔧 Java Collections Methods

**Tags:** #java #oca #collections #list #set #map #methods #lambda  

Essential methods available across all [[Collections|Collection]] implementations with practical examples.

---

## 🔧 Core Collection [[Defining Methods|Methods]]

### ➕ `add(E element)` - Add Elements

Returns `boolean` - indicates success/failure of addition

```java
Collection<String> names = new ArrayList<>();
System.out.println(names.add("John"));    // true

// 🔍 Behavior varies by collection type:
Collection<String> list = new ArrayList<>();
System.out.println(list.add("John"));     // true
System.out.println(list.add("John"));     // true (List allows duplicates)

Collection<String> set = new HashSet<>();
System.out.println(set.add("John"));      // true  
System.out.println(set.add("John"));      // false (Set rejects duplicates)
```

### ➖ `remove(Object element)` - Remove Elements

Returns `boolean` - element was found and removed

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George"); names.add("John");
System.out.println(names);                // [John, George, John]
System.out.println(names.remove("John")); // true (removes first match)
System.out.println(names);                // [George, John]
System.out.println(names.remove("Luke")); // false (element not found)
```

**🔍 Key Points:**

- **🎯 First match only** - Removes only the first occurrence
- **❌ Element not found** - Returns false if element doesn't exist

---

## 📊 Size and Status Methods

### 📏 `size()` - Get Element Count

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George"); names.add("John");
System.out.println(names.size());         // 3
```

### 🕳️ `isEmpty()` - Check if Empty

```java
Collection<String> names = new ArrayList<>();
System.out.println(names.isEmpty());      // true
names.add("John");
System.out.println(names.isEmpty());      // false
```

### 🧹 `clear()` - Remove All Elements

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George");
System.out.println(names.size());         // 2
names.clear();
System.out.println(names.size());         // 0
System.out.println(names.isEmpty());      // true
```

---

## 🔍 Search and Comparison Methods

### 🔍 `contains(Object element)` - Check Element Existence

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George");
System.out.println(names.contains("George")); // true
System.out.println(names.contains("Luke"));   // false
```

### ⚖️ `equals(Object other)` - Compare Collections

Compares type and contents of Collections. **Implementation varies:**

```java
List<String> list1 = Arrays.asList("A", "B", "C");
List<String> list2 = Arrays.asList("A", "B", "C");
Set<String> set1 = new HashSet<>(Arrays.asList("A", "B", "C"));
Set<String> set2 = new HashSet<>(Arrays.asList("C", "B", "A"));

System.out.println(list1.equals(list2));  // true (same order)
System.out.println(set1.equals(set2));    // true (order irrelevant)
System.out.println(list1.equals(set1));   // false (different types)
```

**🔍 Comparison Rules:**

- **📋 ArrayList:** Order matters
- **🔢 HashSet:** Order ignored
- **🆚 Different types:** Always false

---

## ⚡ [[Functional Interfaces and Lambdas|Lambda]]-Enhanced Methods

### 🗑️ `removeIf(Predicate<? super E> filter)` - Conditional Removal

Takes **Predicate** as argument, removes elements matching condition

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George"); names.add("Luke");
System.out.println(names);                 // [John, George, Luke]

names.removeIf(s -> s.length() > 4);       // Remove names longer than 4 chars
System.out.println(names);                 // [John, Luke]

// 🔍 More examples:
numbers.removeIf(n -> n % 2 == 0);         // Remove even numbers
words.removeIf(String::isEmpty);           // Remove empty strings
```

### 🔄 `forEach(Consumer<? super E> action)` - Iterate Through Elements

Takes **Consumer** as argument, performs action on each element

```java
Collection<String> names = new ArrayList<>();
names.add("John"); names.add("George"); names.add("Luke");

names.forEach(name -> System.out.print(name + ", "));
// Output: John, George, Luke,

// 🔍 More examples:
names.forEach(System.out::println);       // Print each on new line
numbers.forEach(n -> System.out.println(n * 2)); // Print doubled values
```

---

## 📊 Method Summary Table

|Method|Return Type|Description|Lambda Type|
|---|---|---|---|
|**➕ `add(E)`**|`boolean`|Adds element|-|
|**➖ `remove(Object)`**|`boolean`|Removes first match|-|
|**📏 `size()`**|`int`|Number of elements|-|
|**🕳️ `isEmpty()`**|`boolean`|Check if empty|-|
|**🧹 `clear()`**|`void`|Remove all elements|-|
|**🔍 `contains(Object)`**|`boolean`|Check element exists|-|
|**🗑️ `removeIf()`**|`boolean`|Remove by condition|**Predicate**|
|**🔄 `forEach()`**|`void`|Iterate elements|**Consumer**|
|**⚖️ `equals(Object)`**|`boolean`|Compare collections|-|

---

## 🔍 Common Patterns

### 🧪 Testing and Filtering

```java
// Check if any element matches condition:
boolean hasLongNames = names.stream().anyMatch(s -> s.length() > 5);

// Remove all elements matching condition:
names.removeIf(s -> s.startsWith("J"));

// Process only certain elements:
names.stream()
     .filter(s -> s.length() > 3)
     .forEach(System.out::println);
```

### 🔄 Bulk Operations

```java
Collection<String> names = new ArrayList<>();
names.addAll(Arrays.asList("John", "George", "Luke"));  // Add multiple
names.retainAll(Arrays.asList("John", "Luke"));         // Keep only these
names.removeAll(Arrays.asList("John"));                 // Remove these
```

---

## 🎯 Key Takeaways

- **🔧 Universal Methods** - All Collection implementations support these core methods
- **📊 Consistent Return Types** - boolean for success/failure, int for counts
- **⚡ Lambda Integration** - removeIf() and forEach() use functional interfaces
- **🔍 Behavior Variations** - Same method, different behavior (Set vs List duplicates)
- **🚫 First Match Removal** - remove() only removes first occurrence
- **⚖️ Implementation-Specific** - equals() behavior depends on collection type
- **💡 Functional Style** - Lambda methods enable concise, readable code

---