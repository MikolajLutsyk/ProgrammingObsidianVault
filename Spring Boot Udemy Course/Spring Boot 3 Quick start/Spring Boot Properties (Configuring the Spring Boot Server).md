# ⚙️ Spring Boot Configuration via `application.properties`  
**Tags:** #spring-boot #configuration #java 

Spring Boot uses the `application.properties` file to configure various aspects of the application. These properties are grouped into categories:

---

## 🔹 Core Properties

### 🔊 Logging Levels (per package)
```properties
logging.level.org.springframework=DEBUG
logging.level.org.hibernate=TRACE
logging.level.com.mluts=INFO
```

**Available Levels:**  
`TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR`, `FATAL`, `OFF`

### 📁 Log Output File
```properties
logging.file.name=logs.log
logging.file.path=c:/myapps/demo
```

---

## 🌐 Web Properties

### 🌍 Server Port
```properties
server.port=7070
```

### 🛣️ Context Path
```properties
server.servlet.context-path=/my-silly-app
```

### ⏱️ Session Timeout
```properties
server.servlet.session.timeout=15m
```

---

## 🔐 Security Properties

### 👤 Default User
```properties
spring.security.user.name=admin
spring.security.user.password=topsecret
```

---

## 🗄️ Data Properties

### 🔗 JDBC Connection
```properties
spring.datasource.url=jdbc:mysql://localhost:3306/ecommerce
spring.datasource.username=kolya
spring.datasource.password=pass
```

---

## 📊 Actuator Endpoints

### ⭐ Expose All Endpoints
```properties
management.endpoints.web.exposure.include=*
```

### 🚫 Exclude Specific Endpoints
```properties
management.endpoints.web.exposure.exclude=health,info
```

### 🔗 Base Path for Actuator
```properties
management.endpoints.web.base-path=/actuator
```

---

