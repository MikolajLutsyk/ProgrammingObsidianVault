## ⚙️ Injecting Custom Properties with @Value
**Tags:** #spring-boot #java 

### 1. Define in `application.properties`

```properties
myapp.timeout=5000
myapp.name=CustomApp
```

### 2. Inject with `@Value`

```java
@Component
public class MyComponent {

    @Value("${myapp.timeout}")
    private int timeout;

    @Value("${myapp.name}")
    private String name;

    public void printProperties() {
        System.out.println("Timeout: " + timeout);
        System.out.println("Name: " + name);
    }
}
```
