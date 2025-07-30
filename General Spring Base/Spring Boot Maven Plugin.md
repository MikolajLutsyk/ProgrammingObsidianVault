# 🔧 Spring Boot Maven Plugin  
**Tags:** #spring-boot #maven #java 

---

## 📦 Description

The **Spring Boot Maven Plugin** simplifies the process of building and running Spring Boot applications with Maven.

It provides tasks to:
- Package the application into an executable JAR
- Run the app directly using `mvn spring-boot:run`
- Manage classpath and dev tools for hot reload

---

## 🚀 Common Commands

```bash
./mvnw spring-boot:run         # Run the application
./mvnw package                 # Package as executable JAR
./mvnw spring-boot:repackage   # Repackage JAR for Spring Boot
```

---

## 🛠️ Plugin Configuration (in `pom.xml`)

```xml
<plugin>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
```

> ✅ Automatically included with `spring-boot-starter-parent`.

