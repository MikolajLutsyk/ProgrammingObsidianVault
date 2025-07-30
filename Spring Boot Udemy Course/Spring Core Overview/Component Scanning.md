# 🔍 Component Scanning & `@SpringBootApplication` in Spring Boot  
**Tags:** #spring-boot #component-scanning #configuration #java 

---

## 📌 Overview

Spring Boot automatically scans Java classes for special annotations (e.g., `@Component`, `@Service`, `@Repository`) and registers them as beans in the Spring IoC container. This process simplifies configuration and promotes a modular design.

---

## 🔧 How It Works

### 1. Component Scanning

- **Default Behavior**:  
  Spring Boot starts component scanning from the same package where the main application class is located and recursively scans all sub-packages.  
  > This implicitly defines a **base search package**, so there's no need to explicitly specify it.

- **Explicit Configuration**:  
  You can explicitly define a list of base packages to scan using the `@ComponentScan` annotation:
  ```java
  @ComponentScan(basePackages = {"com.example.package1", "com.example.package2"})
  ```

---

## 🛠️ `@SpringBootApplication` Annotation

The `@SpringBootApplication` annotation is a meta-annotation that combines the following:

- **`@EnableAutoConfiguration`**:  
  Enables Spring Boot's auto-configuration, which automatically configures your application based on the dependencies present in the classpath.

- **`@ComponentScan`**:  
  Scans for components in the current package and its sub-packages, eliminating the need to declare this manually.

- **`@Configuration`**:  
  Allows you to register extra beans using the `@Bean` annotation or import additional configuration classes.

**Example:**

```java
@SpringBootApplication  
public class SpringCoreDemoApplication {  
    public static void main(String[] args) {  
        SpringApplication.run(SpringCoreDemoApplication.class, args);  
    }  
}
```

---

## 📚 More on Component Scanning

- **Default Behavior**:  
  The application automatically starts scanning from the package of the main class, as well as recursively scanning all sub-directories.
  
- **Customization**:  
  To change the default behavior, explicitly provide base packages in the `@ComponentScan` annotation.

### Example of Explicit Component Scanning:

```java
@SpringBootApplication  
@ComponentScan(basePackages = {"com.example.services", "com.example.repositories"})
public class CustomComponentScanApplication {  
    public static void main(String[] args) {  
        SpringApplication.run(CustomComponentScanApplication.class, args);  
    }  
}
```

In this example, Spring Boot will scan the packages `com.example.services` and `com.example.repositories`, regardless of where the main class is located.

Component scanning is the base for [[Defining Dependency Injection|Dependency Injection]]

