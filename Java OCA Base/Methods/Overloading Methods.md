# 🔄 Java [[Defining Methods|Method]] Overloading

**Tags:** #java #methods #overloading #polymorphism

Method overloading allows multiple methods with the same name but different parameter lists in the same class.

---

## 🎯 Basic Concept

**Overloading**: Having two or more methods with the same name but different parameter lists.

```java
public void greet(int x) { 
    System.out.println("Hello"); 
}

public void greet(double x) { 
    System.out.println("Good Afternoon"); 
}

public void greet(int x, int y) { 
    System.out.println("Good Day"); 
}
```

### 📋 Method Call Examples

- `greet(5);` → "Hello"
- `greet(3.14);` → "Good Afternoon"
- `greet(7, -11);` → "Good Day"

---

## 🔄 Type Matching & Promotion

When the argument doesn't exactly match a parameter type, Java picks the **most similar** version of the method.

### 📈 Primitive Type Promotion

```java
public void greet(int x) { System.out.println("Hello"); }
public void greet(double x) { System.out.println("Good Afternoon"); }

short a = 2;
greet(a); // No greet(short x), so Java promotes to int → "Hello"
```

### 📦 Wrapper Class Matching

```java
public void greet(Short a) { System.out.println("Hi"); }
public void greet(Integer a) { System.out.println("Hello"); }
public void greet(String str) { System.out.println("Good Afternoon"); }
public void greet(Object o) { System.out.println("Good Day"); }
```

#### 🎯 Wrapper Examples

- `greet(2.3);` → wraps `2.3` in `Double`, which extends `Object` → "Good Day"
- `greet((short)2);` → wraps to `Short` → "Hi"
- `greet((byte)3);` → wraps to `Byte`, which extends `Object` → "Good Day"
- `greet("John Wayne");` → "Good Afternoon"

---

## 🏗️ Supertype Matching

Java also looks for **supertypes** when finding matches.

```java
public void greet(Number a) { System.out.println("Hi"); }
public void greet(CharSequence a) { System.out.println("Hello"); }
public void greet(Object o) { System.out.println("Good Day"); }
```

### 🎯 Supertype Examples

- `greet(3.14);` → wraps `3.14` to `Double`, which implements `Number` → "Hi"
- `greet("Luke");` → `String` implements `CharSequence` → "Hello"
- `greet(new int[]{1, 2, 3});` → can't find anything similar → "Good Day"

---

## ⚠️ Important Restriction: Arrays vs Varargs

### 🚫 Cannot Overload [[Arrays]] with [[Variable Arguments (Varargs)|Varargs]]

```java
public int doSomething(int[] nums) { }      // Array parameter
public int doSomething(int... nums) { }     // Varargs parameter
// ❌ DOES NOT COMPILE - Ambiguous methods

doSomething(new int[]{1, 2, 3, 4, 5}); // Which method to call?
```

**Why?** Java treats varargs and arrays as equivalent for method resolution, creating ambiguity.

---

## 📊 Method Resolution Priority

When Java resolves overloaded methods, it follows this priority:

1. **🎯 Exact match** - Same parameter types
2. **📈 Primitive promotion** - Widening primitives (short → int → long → float → double)
3. **📦 Autoboxing** - Primitive to wrapper (int → Integer)
4. **🏗️ Supertype matching** - Parent classes/interfaces
5. **🌍 Object fallback** - Most general type (Object)

---