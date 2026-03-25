# 🌱 Spring Core Concepts

## 1. Inversion of Control (IoC)
**Definition:**  
- IoC is a design principle where the control of object creation and dependency management is transferred from the application code to a container (Spring IoC Container).  

- Instead of the application instantiating objects directly, the container manages them.

**Example:**
```java
// Without IoC
Service service = new ServiceImpl();
Client client = new Client(service);

// With IoC (Spring manages creation)
ApplicationContext context = new ClassPathXmlApplicationContext("beans.xml");
Client client = context.getBean(Client.class);
```

## 2. Dependency Injection (DI)
**Definition**:  
- DI is the process of providing dependencies to a class from the outside rather than creating them inside the class.

- Spring supports constructor injection and setter injection.

Example: Constructor Injection

```
@Component
public class Client {
    private final Service service;

    @Autowired
    public Client(Service service) {
        this.service = service;
    }

    public void doWork() {
        service.perform();
    }
}
```

## 3. Bean & ApplicationContext
- Bean: An object managed by the Spring IoC container.

- ApplicationContext: The central interface to access beans and manage their lifecycle.

```
@Configuration
@ComponentScan("com.example")
public class AppConfig {}

public class MainApp {
    public static void main(String[] args) {
        ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
        Client client = context.getBean(Client.class);
        client.doWork();
    }
}
```

## 4. Bean Lifecycle (Concept)
Spring beans go through several stages:

Instantiation – Bean is created.

Dependency Injection – Dependencies are injected.

Initialization – Custom init methods are called.

Ready to use – Bean is available for use.

Destruction – Bean is destroyed when the context is closed.

```
@Component
public class MyBean {

    @PostConstruct
    public void init() {
        System.out.println("Bean is initialized");
    }

    @PreDestroy
    public void destroy() {
        System.out.println("Bean is being destroyed");
    }
}
```

## 5. @Component and @Configuration
- @Component: Marks a class as a Spring-managed bean.

- @Configuration: Indicates that a class contains bean definitions (used with @Bean methods).

Example:
```
@Component
public class ServiceImpl implements Service {
    @Override
    public void perform() {
        System.out.println("Service is performing work");
    }
}

@Configuration
public class AppConfig {
    @Bean
    public Service service() {
        return new ServiceImpl();
    }
}
```

## Conclusion
- Spring Core Concepts revolve around IoC and DI, enabling loose coupling and easier testing.
- Beans are the fundamental building blocks, managed by the ApplicationContext, with a well-defined lifecycle.
- Annotations like @Component and @Configuration simplify bean registration and configuration.