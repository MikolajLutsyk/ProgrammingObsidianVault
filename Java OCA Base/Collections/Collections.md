# 📚 Java Collections Overview

**Tags:** #java #oca #collections #list #set #map #lambda  

Collections are the foundation for storing and organizing groups of objects in Java.

---

## 🎯 What is a Collection?

**Collections** are [[Interface Basics|interfaces]] that provide standardized ways to store and manipulate groups of objects:

- **📋 List** - Ordered, allows duplicates
- **🔢 Set** - Unordered, no duplicates
- **🚶 Queue (Deque)** - FIFO/LIFO operations
- **🗺️ Map** - Key-value pairs

---

## 🏗️ Collections Hierarchy

```java
// Collection Interface Implementations:
Collection
├── List ←── ArrayList, LinkedList
├── Set  ←── HashSet, TreeSet
└── Queue ←── LinkedList (also implements List)

// Separate hierarchy:
Map ←── HashMap, TreeMap (doesn't implement Collection)
```

### 🔍 Key Implementation Details:

- **📋 ArrayList** - Better for **reading** more than writing
- **🔗 LinkedList** - Implements both **List** and **Deque**
- **🔢 HashSet** - Fast lookup, no order guarantee
- **🌳 TreeSet** - Sorted set implementation
- **🗺️ HashMap** - Key-value pairs, fast access
- **🌳 TreeMap** - Sorted map implementation

---

## 💎 Diamond Operator Syntax

```java
// ✅ Valid declarations:
List<String> names = new ArrayList<>();           // Diamond operator
List<String> names = new ArrayList<String>();     // Full type
var names = new ArrayList<String>();              // var (Java 17+)

// ❌ Invalid declarations:
List<> names = new ArrayList<>();                 // Missing left type
var names = new ArrayList<>();                    // Missing right type
```

**🔍 Diamond Operator Rules:**

- **⬅️ Left side:** Must specify type OR use `var`
- **➡️ Right side:** Can omit type with `<>` OR must specify with `var`
- **🏗️ Declaration flexibility:** Can use class name (ArrayList) or interface name (List/Collection)

---

## 🆚 Collection Type Comparison

|Type|Ordered|Duplicates|Key Features|
|---|---|---|---|
|**📋 List**|✅ Yes|✅ Yes|Index-based access, dynamic sizing|
|**🔢 Set**|❌ No*|❌ No|Unique elements, fast lookup|
|**🚶 Queue**|✅ Yes|✅ Yes|FIFO/LIFO operations|
|**🗺️ Map**|❌ No*|❌ No|Key-value pairs, unique keys|

*TreeSet and TreeMap maintain sorted order

---

## 🎯 When to Use Which Collection

### 📋 Use List When:

- **📊 Order matters** - Need to maintain insertion order
- **🔄 Duplicates allowed** - Same elements can appear multiple times
- **🔢 Index access** - Need to access elements by position
- **📈 Dynamic sizing** - Size changes frequently

### 🔢 Use Set When:

- **🚫 No duplicates** - Need unique elements only
- **🔍 Fast lookup** - Need to check if element exists quickly
- **🧹 Deduplication** - Want to remove duplicates from data

### 🚶 Use Queue When:

- **📥 FIFO operations** - First in, first out processing
- **📤 LIFO operations** - Last in, first out (with Deque)
- **🔄 Sequential processing** - Processing elements in order

### 🗺️ Use Map When:

- **🔑 Key-value pairs** - Need to associate keys with values
- **🔍 Fast lookup by key** - Need quick access to values via keys
- **📇 Dictionary-like** - Creating lookup tables or mappings

---

## 🎯 Key Takeaways

- **📚 Four Main Types** - List, Set, Queue, Map (Map separate from Collection)
- **🏗️ Multiple Implementations** - Each interface has various concrete classes
- **💎 Modern Syntax** - Use diamond operator for cleaner code
- **🆚 Choose Appropriately** - Select collection type based on use case
- **🔍 Behavior Differences** - Each type has unique characteristics (duplicates, ordering, etc.)
- **⚡ Performance Considerations** - ArrayList vs LinkedList, HashSet vs TreeSet

---