# ⏳ Java Periods, Durations & Instants Reference

**Tags:** #java #datetime #period #duration #instant

Three classes for measuring time spans and timestamps: Period (date-based), Duration (time-based), and Instant (timestamp).

---

## 📅 Period (Date-based)

### 🗓️ Creating Periods

```java
Period p1 = Period.ofYears(2);     // P2Y
Period p2 = Period.ofMonths(3);    // P3M
Period p3 = Period.ofWeeks(1);     // P7D
Period p4 = Period.ofDays(11);     // P11D
Period p5 = Period.of(2, 0, 15);   // P2Y15D (years, months, days)
```

**Usage:** Only with `LocalDate` and `LocalDateTime`.

Periods and Durations in [[Create Dates and Times]]
### ➕ Using Periods 

```java
Period period = Period.of(1, 2, 5);  // 1 year, 2 months, 5 days
LocalDate date = LocalDate.of(2022, 11, 20);

date = date.plus(period);   // 2023-01-25
date = date.minus(period);  // 2022-11-20
```

---

## ⏰ Duration (Time-based)

### 🕐 Creating Durations

```java
Duration d1 = Duration.ofDays(3);      // PT72H
Duration d2 = Duration.ofHours(2);     // PT2H
Duration d3 = Duration.ofMinutes(45);  // PT45M
Duration d4 = Duration.ofSeconds(10);  // PT10S
Duration d5 = Duration.ofMillis(240);  // PT0.24S
Duration d6 = Duration.ofNanos(2503);  // PT0.000002503S
```

**Usage:** Only with `LocalTime` and `LocalDateTime`.

### 🔧 Using ChronoUnit

```java
import java.time.temporal.*;

Duration d0 = Duration.of(3, ChronoUnit.HALF_DAYS); // PT36H
Duration d1 = Duration.of(3, ChronoUnit.DAYS);      // PT72H
Duration d2 = Duration.of(2, ChronoUnit.HOURS);     // PT2H
Duration d3 = Duration.of(45, ChronoUnit.MINUTES);  // PT45M
```

### 📏 Measuring Time Between

```java
LocalTime t1 = LocalTime.of(17, 30);
LocalTime t2 = LocalTime.of(20, 45);

System.out.println(ChronoUnit.HOURS.between(t1, t2));   // 3
System.out.println(ChronoUnit.MINUTES.between(t1, t2)); // 195
```

### ➕ Using Durations

```java
LocalTime time = LocalTime.of(17, 30);
Duration d3 = Duration.ofMinutes(45);

time = time.plus(d3);   // 18:15
time = time.minus(d3);  // 17:30
```

---

## ⚡ Instant (Timestamps)

### 📸 Recording Timestamps

```java
Instant now = Instant.now();
System.out.println(now); // 2023-04-18T09:20:52.904935284Z
```

### ⏱️ Measuring Process Duration

```java
Instant before = Instant.now();
// ... time-consuming process
Instant after = Instant.now();

Duration dur = Duration.between(before, after);
System.out.println(dur.toMillis()); // 255 (milliseconds)
```

### 🔄 Converting from ZonedDateTime

```java
ZoneId zone = ZoneId.of("Europe/Zagreb");
ZonedDateTime z = ZonedDateTime.of(2022, 11, 2, 21, 50, 14, 145, zone);
Instant inst = z.toInstant();

System.out.println(inst); // 2022-11-02T20:50:14.000000145Z
```

### 💾 Under the Hood

**Epoch Time:** Instant uses a long representing seconds since 1970-01-01T00:00:00Z (Java epoch).

---