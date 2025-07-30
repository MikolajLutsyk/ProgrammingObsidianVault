# 📅 Java Date/Time API

**Tags:** #java #datetime #time #date #timezone

Java provides four main Date/Time types in the `java.time` package for handling different temporal scenarios.

---

## 🔹 Four Main Types

### 📦 Import Statement

```java
import java.time.*;
```

### 🕐 Current Date/Time

```java
LocalDate now1 = LocalDate.now();        // Date only
LocalTime now2 = LocalTime.now();        // Time only  
LocalDateTime now3 = LocalDateTime.now(); // Date + Time
ZonedDateTime now4 = ZonedDateTime.now(); // Date + Time + Timezone

System.out.println(now1); // 2023-04-16
System.out.println(now2); // 12:12:51.372755660
System.out.println(now3); // 2023-04-16T12:12:51.372980941
System.out.println(now4); // 2023-04-16T12:12:51.373473327Z[GMT]
```

---

## 📆 Creating LocalDate

### 🗓️ Date Creation

```java
LocalDate d1 = LocalDate.of(2022, Month.NOVEMBER, 2);
LocalDate d2 = LocalDate.of(2022, 11, 2);  // Using numeric month

System.out.println(d1); // 2022-11-02
```

**Options:** Use `Month` enum or numeric month (1-12).

---

## ⏰ Creating LocalTime

### 🕒 Time Creation

```java
LocalTime t1 = LocalTime.of(21, 50);           // Hour, minute
LocalTime t2 = LocalTime.of(21, 50, 14);       // Hour, minute, second
LocalTime t3 = LocalTime.of(21, 50, 14, 145);  // Hour, minute, second, nanosecond

System.out.println(t3); // 21:50:14.000000145
```

**Precision:** Supports nanosecond precision for high accuracy.

---

## 📅 Creating LocalDateTime

### 🗓️ DateTime Creation

```java
// Method 1: All parameters
LocalDateTime dt1 = LocalDateTime.of(2022, Month.NOVEMBER, 2, 21, 50, 14);

// Method 2: Combine LocalDate and LocalTime
LocalDate d1 = LocalDate.of(2022, Month.NOVEMBER, 2);
LocalTime t3 = LocalTime.of(21, 50, 14, 145);
LocalDateTime dt2 = LocalDateTime.of(d1, t3);

System.out.println(dt2); // 2022-11-02T21:50:14.000000145
```

**Flexibility:** Create from individual components or combine existing date/time objects.

---

## 🌍 Creating ZonedDateTime

### 🗺️ Timezone-Aware DateTime

```java
ZoneId zone = ZoneId.of("Europe/Zagreb");
ZonedDateTime z1 = ZonedDateTime.of(2022, 11, 2, 21, 50, 14, 145, zone);

System.out.println(z1); // 2022-11-02T21:50:14.000000145+01:00[Europe/Zagreb]
```

**Components:** Includes timezone offset (`+01:00`) and timezone identifier (`[Europe/Zagreb]`).

---

## 🔄 Timezone Conversion

### 🧮 Converting to GMT

```java
// Example 1: +05:30 offset (ahead of GMT)
// 2022-11-02T13:50+05:30[] => GMT: 2022-11-02 08:20
// Calculation: 13:50 - 05:30 = 08:20

// Example 2: -05:00 offset (behind GMT)  
// 2022-11-02T06:10-05:00[] => GMT: 2022-11-02 11:10
// Calculation: 06:10 - (-05:00) = 06:10 + 05:00 = 11:10
```

**Rule:** Subtract the offset from local time to get GMT.

- **Positive offset** (+): Subtract normally
- **Negative offset** (-): Subtracting negative = addition

### 📝 Conversion Examples

```java
// Local time: 14:30 with offset +03:00
// GMT time: 14:30 - 03:00 = 11:30

// Local time: 09:15 with offset -07:00  
// GMT time: 09:15 - (-07:00) = 09:15 + 07:00 = 16:15
```

---