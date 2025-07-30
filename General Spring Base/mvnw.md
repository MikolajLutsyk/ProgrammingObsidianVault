# 🧰 Maven Wrapper (`mvnw`) in Spring Boot Projects  
**Tags:** #spring-boot #maven #java 

---

## 📁 Location
- `mvnw` (Unix)
- `mvnw.cmd` (Windows)
- `.mvn/wrapper/` (directory in project root)

---

## 🎯 Purpose
- ✅ Provides a **self-contained Maven setup**
- ✅ Ensures **consistent builds** across different environments
- ✅ Avoids requiring a local Maven installation
- ✅ Uses a **project-specific Maven version** (defined in `.mvn/wrapper/maven-wrapper.properties`)

---

## 📄 Key Files

| File                                 | Purpose                              |
|--------------------------------------|--------------------------------------|
| `mvnw` / `mvnw.cmd`                  | Shell/batch scripts to run Maven     |
| `.mvn/wrapper/maven-wrapper.jar`     | Wrapper logic                        |
| `.mvn/wrapper/maven-wrapper.properties` | Specifies the Maven version to use |

---

## 🛠️ Usage

Run Maven commands via the wrapper:

```bash
./mvnw spring-boot:run     # Run the Spring Boot app
./mvnw clean install       # Clean and build the project
```

> 💡 Use `./mvnw` instead of `mvn` to ensure the correct Maven version is used.
