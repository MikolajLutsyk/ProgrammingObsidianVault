# 📦 Java Boxing & Unboxing

**Tags:** #java #boxing #unboxing #autoboxing #primitives

Boxing converts primitives to [[Wrapper Classes|wrapper]] objects, unboxing does the reverse. Java can do this automatically but with limitations.

---

## 🔹 Explicit Conversion

### 📥 Boxing (Primitive → Wrapper)

```java
int a = 3;
Integer b = Integer.valueOf(a);  // Explicit boxing
```

### 📤 Unboxing (Wrapper → Primitive)

```java
Integer b = 5;
int c = b.intValue();  // Explicit unboxing
```

---

## ⚡ Automatic Conversion

### 🔄 Autoboxing & Auto-unboxing

```java
int a = 3;
Integer b = a;  // Autoboxing: int → Integer
int c = b;      // Auto-unboxing: Integer → int
```

---

## ⚠️ Autocasting Limitation

### ❌ Cannot Do Both Operations

```java
int x = 7;
long y = x;     // ✅ Autocasting only
Long z = x;     // ❌ Autocasting + autoboxing together
```

### ✅ Solutions - Do One Manually

```java
int x = 7;

// Option 1: Explicit boxing
Long z = Long.valueOf(x);

// Option 2: Explicit casting  
Long z = (long) x;

// Option 3: Both explicit
Long z = Long.valueOf((long) x);
```

---

## 🔢 Literal Assignments

### 📝 Primitive Literals

```java
Long x = 10;   // ❌ Requires autocasting int→long + autoboxing
Long y = 10L;  // ✅ Only autoboxing needed (long literal)
```

**Rule:** Java won't do autocasting and autoboxing simultaneously.

---