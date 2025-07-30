# 🚀 Running a Spring Boot App  
**Tags:** #spring-boot #java 

There are two ways to run a Spring Boot application:

---

### ✅ Option 1: Using `java -jar`

- Requires packaging the app first
- No need to install Maven or any extra tools — self-contained

**Steps:**
```bash
./mvnw package
java -jar target/mydemoapp-0.0.1-SNAPSHOT.jar
```

---

### ✅ Option 2: Using [[Spring Boot Maven Plugin]]

- Uses `./mvnw` ([[mvnw | Maven Wrapper]]) to install the correct Maven version automatically if it's not present
- Ideal for consistent builds across environments

**Steps:**
```bash
./mvnw spring-boot:run
```

If Maven is already installed, you can use `mvn` instead of `./mvnw`.

---

### 📦 Summary of Commands

| Task         | Option 1 (`java -jar`)               | Option 2 (`spring-boot:run`)     |
|--------------|--------------------------------------|----------------------------------|
| **Package**  | `./mvnw package`                     | `./mvnw package`                 |
| **Run**      | `java -jar target/mydemoapp-0.0.1-SNAPSHOT.jar` | `./mvnw spring-boot:run`         |
