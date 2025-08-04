# ⏰ Java Date/Time [[Defining Methods|Methods]] 

**Tags:** #java #datetime #methods #oca 

[[Create Dates and Times|Date and Time]] [[Class Basics|classes]] provide plus/minus methods for manipulation and comparison methods for ordering.

---

## ➕ Addition Methods

### 📅 LocalDate & LocalDateTime

```java
LocalDate date = LocalDate.of(2022, Month.NOVEMBER, 15);
date = date.plusDays(4);    // 2022-11-19
date = date.plusWeeks(2);   // 2022-12-03
date = date.plusMonths(3);  // 2023-03-03
date = date.plusYears(1);   // 2024-03-03
```

### 🕐 LocalTime & LocalDateTime

```java
LocalDateTime dateTime = LocalDateTime.of(2022, Month.NOVEMBER, 15, 17, 30);
dateTime = dateTime.plusHours(3);   // 2022-11-15T20:30
dateTime = dateTime.plusMinutes(15); // 2022-11-15T20:45
dateTime = dateTime.plusSeconds(30); // 2022-11-15T20:45:30
dateTime = dateTime.plusNanos(500);  // 2022-11-15T20:45:30.000000500
```

---

## ➖ Subtraction Methods

### 📉 Minus Operations

```java
LocalDateTime dateTime = LocalDateTime.of(2022, Month.NOVEMBER, 15, 17, 30);
dateTime = dateTime.minusDays(5);     // 2022-11-10T17:30
dateTime = dateTime.minusHours(2);    // 2022-11-10T15:30
dateTime = dateTime.minusMinutes(15); // 2022-11-10T15:15
```

---

## 🔗 Method Chaining

### ⛓️ Chained Operations

```java
LocalDateTime dateTime = LocalDateTime.of(2022, Month.NOVEMBER, 15, 17, 30);
dateTime = dateTime.minusDays(5).plusHours(6).minusSeconds(45);
// Result: 2022-11-10T23:29:15
```

---

## 🔒 Immutability Warning

### ❌ Common Mistake

```java
LocalDate date = LocalDate.of(1980, 4, 1);
date.plusDays(20);           // Does nothing!
System.out.println(date);    // Still: 1980-04-01
```

### ✅ Correct Usage

```java
LocalDate date = LocalDate.of(1980, 4, 1);
date = date.plusDays(20);    // Reassign the result
System.out.println(date);    // Now: 1980-04-21
```

---

## ⚖️ Comparison Methods

### 📊 Before/After Comparison

```java
LocalDate date1 = LocalDate.of(2022, 11, 3);
LocalDate date2 = LocalDate.of(2022, 12, 3);

System.out.println(date1.isBefore(date2)); // true
System.out.println(date1.isAfter(date2));  // false
```

---