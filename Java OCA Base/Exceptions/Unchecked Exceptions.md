# ❌ Java Unchecked [[Exceptions]]

**Tags:** #java #unchecked-exceptions #runtime-exceptions #oca 

Unchecked exceptions may or may not be handled - handling is optional.

---

## 🎯 What Are Unchecked Exceptions?

**Unchecked Exceptions** have optional handling:

- **🔄 Optional handling** - May or may not be handled
- **📋 RuntimeException subclasses** - [[Inheritance|Inherit]] from RuntimeException
- **⚡ Runtime occurrence** - Happen during program execution
- **🔧 No compile requirement** - Code compiles without handling

---

## 📊 Common Unchecked Exceptions

|Exception|Cause|Example|
|---|---|---|
|**➗ ArithmeticException**|Division by zero|`10 / 0`|
|**📊 ArrayIndexOutOfBoundsException**|Illegal array index|`arr[999]` when arr.length = 3|
|**🎭 ClassCastException**|Invalid casting|`(String) new Integer(5)`|
|**🚫 NullPointerException**|Null reference usage|`null.toString()`|
|**📝 IllegalArgumentException**|Invalid method argument|Custom validation|
|**🔢 NumberFormatException**|String to number conversion|`Integer.parseInt("abc")`|

**🔍 Note:** NumberFormatException is a subclass of IllegalArgumentException.

---

## ❌ Unhandled Exception Example

```java
public class MyClass {
    private static void printFourthElement(int[] a) {
        System.out.println(a[3]);  // Array only has 3 elements!
    }
    
    public static void main(String args[]) {
        int[] a = {-7, 11, 3};
        printFourthElement(a);
    }
}
```

**🔥 Runtime Output:**

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException:
Index 4 out of bounds for length 3
at MyClass.printFourthElement(MyClass.java:11)
at MyClass.main(MyClass.java:6)
```

---

## ✅ Handled Exception Example

```java
public class MyClass {
    private static void printFourthElement(int[] a) {
        try {
            System.out.println(a[3]);
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("There is no fourth element in the array. Sorry.");
        }
    }
    
    public static void main(String args[]) {
        int[] a = {-7, 11, 3};
        printFourthElement(a);
    }
}
```

**✅ Output:**

```
There is no fourth element in the array. Sorry.
```

---

## ⚡ Manually Throwing Exceptions

```java
public class Student {
    private int id;
    private String fullName;
    
    public Student(int id, String fullName) {
        if (id < 10 || fullName.length() > 100) {
            throw new IllegalArgumentException();  // Manual throw
        }
        this.id = id;
        this.fullName = fullName;
    }
}

// Usage:
Student student = new Student(1, "John Wayne");  // Throws IllegalArgumentException
```

---

## 🎯 Unchecked Exception Characteristics

### ⚡ **Runtime Behavior:**

- **🔧 Optional handling** - Code compiles without try-catch
- **💥 Program termination** - Unhandled exceptions crash program
- **🛡️ Graceful handling** - try-catch provides better user experience

### 🔍 **Common Causes:**

- **🧮 Programming errors** - Logic mistakes, invalid assumptions
- **📊 Data validation** - Invalid input, boundary conditions
- **🚫 Null references** - Accessing methods/fields on null objects

---

## 🎯 Key Takeaways

- **❌ Optional Handling** - No compile-time requirement to handle
- **⚡ Runtime Exceptions** - Subclasses of RuntimeException
- **💥 Program Impact** - Unhandled exceptions terminate program
- **🛡️ Better Practice** - Handle for graceful error recovery
- **⚡ Manual Throwing** - Can throw programmatically with throw keyword
- **🔍 Common Types** - Arithmetic, Array, Null, Cast, Argument exceptions

---