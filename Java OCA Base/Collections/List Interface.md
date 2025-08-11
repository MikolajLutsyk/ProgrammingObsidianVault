# 📋 Java List Interface and Methods

**Tags:** #java #oca #ocp #list #collections #methods #factory-methods #lambda

List is an ordered [[Collections|collection]] that can contain duplicate entries with index-based access.

---

## 🎯 What is a List?

**List** is an ordered collection interface with these characteristics:

- **📊 Ordered** - Elements maintain insertion order
- **🔄 Duplicates** - Can contain duplicate entries
- **🔢 Index Access** - Items accessed/inserted using index (int)
- **📈 Dynamic Size** - Can change size after declaration (unlike arrays)

### 🏗️ Implementation [[Class Basics|Classes]]

- **📋 ArrayList** - Better for **reading** more than writing
- **🔗 LinkedList** - Implements both **List** and **Deque**
- **📝 OCA Exam:** Only need to know ArrayList

---

## 💎 Diamond Operator Rules

```java
// ✅ Valid declarations:
List<String> names = new ArrayList<>();           // Diamond operator
List<String> names = new ArrayList<String>();     // Full type  
var names = new ArrayList<String>();              // var (Java 17+ OCP)

// ❌ Invalid declarations:
List<> names = new ArrayList<>();                 // Missing left type
var names = new ArrayList<>();                    // Missing right type with var
```

**🔍 Key Rules:**

- **⬅️ Left side:** Can use class name (ArrayList) or interface name (List/Collection)
- **➡️ Right side:** Type can be omitted with `<>` unless using `var`

---

## 🏭 Factory [[Defining Methods|Methods]]

### 🔹 `Arrays.asList(varargs)` - Fixed Size, Backed by [[Arrays|Array]]

```java
String[] names = {"John", "George", "Luke"};
List<String> namesAsList = Arrays.asList(names);
names[1] = "Ben";                          // Changes array
System.out.println(namesAsList);          // [John, Ben, Luke] - list reflects change

namesAsList.set(2, "Paul");               // Changes list  
System.out.println(Arrays.toString(names)); // [John, George, Paul] - array reflects change

// ❌ Cannot change size:
namesAsList.add("Mike");                   // DOES NOT COMPILE
namesAsList.remove("John");                // DOES NOT COMPILE
```

### 🔹 `List.of(varargs)` - Immutable List

```java
List<String> namesOf = List.of("John", "George", "Luke");
// ❌ Completely immutable:
namesOf.add("Mike");                       // DOES NOT COMPILE
namesOf.remove("John");                    // DOES NOT COMPILE
namesOf.set(0, "Paul");                    // DOES NOT COMPILE
```

### 🔹 `List.copyOf(collection)` - Immutable Copy

```java
List<String> namesCopyOf = List.copyOf(namesAsList);
// ❌ Immutable copy:
namesCopyOf.set(0, "Paul");                // DOES NOT COMPILE
```

---

## 🔧 List-Specific Methods

```java
List<String> names = new ArrayList<>();
names.add("John");                         // [John]
names.add("George");                       // [John, George]
names.add("Paul");                         // [John, George, Paul]
names.add("Ringo");                        // [John, George, Paul, Ringo]

names.add(1, "Luke");                      // [John, Luke, George, Paul, Ringo]
System.out.println(names.get(0));         // John
names.set(3, "Ben");                       // [John, Luke, George, Ben, Ringo]
names.remove(1);                           // [John, George, Ben, Ringo] (by index)
names.remove("Ben");                       // [John, George, Ringo] (by element)
names.replaceAll(s -> s + " A.");          // [John A., George A., Ringo A.]
names.forEach(name -> System.out.print(name + ", ")); // John A., George A., Ringo A.,
```

### 📊 Method Reference

|Method|Description|Example|
|---|---|---|
|**➕ `add(E element)`**|Add to end|`list.add("John")`|
|**📍 `add(int index, E element)`**|Add at index|`list.add(1, "Luke")`|
|**🔍 `get(int index)`**|Get element at index|`list.get(0)`|
|**➖ `remove(int index)`**|Remove by index|`list.remove(1)`|
|**🗑️ `remove(E element)`**|Remove by element|`list.remove("John")`|
|**🔄 `replaceAll(UnaryOperator<E>)`**|Transform all elements|`list.replaceAll(s -> s.toUpperCase())`|
|**📝 `set(int index, E element)`**|Replace at index|`list.set(3, "Ben")`|
|**📈 `sort(Comparator<? super E>)`**|Sort elements|`list.sort(String::compareTo)`|

---

## ⚠️ Remove Method Gotcha

**🔍 Integer List Removal:**

```java
List<Integer> nums = new ArrayList<>();
nums.add(2); nums.add(-11); nums.add(7);  // [2, -11, 7]

nums.remove(2);                            // Removes INDEX 2 → [2, -11]
nums.remove(Integer.valueOf(2));           // Removes ELEMENT 2 → [-11, 7]
```

**🔍 Rules:**

- **🔢 `remove(int)`** - Removes by **index**
- **📦 `remove(Object)`** - Removes by **element**
- **⚡ Primitive int** - Calls `remove(int index)`
- **📦 Integer object** - Calls `remove(Object element)`

---

## 🔄 Converting List to Array

### 🔹 `toArray()` Methods

```java
List<Integer> myList = new ArrayList<>();
myList.add(3); myList.add(5); myList.add(7);

// 📦 Generic Object array:
Object[] objArray = myList.toArray();

// 🔢 Typed Integer array:
Integer[] intArray = myList.toArray(new Integer[0]);
// Size 0 is fine - Java automatically adjusts to fit
```

---

## 🏗️ Constructor Variations

```java
// 🆕 Empty list:
List<String> myList1 = new ArrayList<>();

// 📋 Copy constructor:
List<String> myList2 = new ArrayList<>(myList1);

// 📏 Initial capacity (still can grow):
ArrayList<String> arrayList3 = new ArrayList<>(5);
```

---

## 🎯 Key Takeaways

- **📋 List Interface** - Ordered, allows duplicates, index-based access
- **🏗️ Implementations(concrete [[Class Basics|classes]])** - ArrayList (better for reading), LinkedList (List + Deque)
- **🏭 Factory Methods** - Arrays.asList() (backed), List.of() (immutable), List.copyOf() (immutable copy)
- **💎 Diamond Operator** - Use `<>` for cleaner syntax, follow var rules
- **🔧 Index Operations** - add(), get(), set(), remove() by index
- **⚠️ Remove Gotcha** - Primitive int = index, Integer object = element
- **🔄 Array Conversion** - toArray() for Object[], toArray(T[]) for typed arrays
- **📏 Dynamic Sizing** - Unlike arrays, Lists can grow and shrink

---