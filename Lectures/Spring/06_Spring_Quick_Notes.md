# Quick Notes: Spring Framework & Core Concepts

## 1. Spring Framework Overview
- **Explanation**:  
  Spring is a comprehensive framework for enterprise Java development. It provides infrastructure support for building applications, focusing on modularity, testability, and loose coupling.

- **Benefits of Spring**:
  1. Simplifies enterprise application development.
  2. Promotes loose coupling via IoC and DI.
  3. Rich ecosystem (Spring Web, Spring Data, Spring Security).
  4. Easy integration with other technologies.

---

## 2. Spring vs Spring Boot
- **Comparison**:
  - **Spring Framework**: Core features, requires manual configuration, XML or Java-based setup.
  - **Spring Boot**: Built on Spring, provides auto-configuration, embedded server, starter dependencies, reduces boilerplate.

- **Auto-Configuration Concept**:
  - Spring Boot automatically configures beans based on classpath dependencies.
  - Example: If `spring-boot-starter-data-jpa` is present, JPA repositories are auto-configured.
  - Customizable via `application.properties` or `application.yml`.

---

## 3. Inversion of Control (IoC) & Dependency Injection (DI)
- **IoC**: Principle where the framework controls object creation and lifecycle instead of developers.
- **DI**: Technique to inject dependencies into classes rather than creating them manually.

### Example
```java
@Service
public class StudentService {
    public String getStudentInfo() {
        return "Student: Hana, Active";
    }
}

@RestController
public class StudentController {
    private final StudentService studentService;

    @Autowired
    public StudentController(StudentService studentService) {
        this.studentService = studentService;
    }

    @GetMapping("/student")
    public String student() {
        return studentService.getStudentInfo();
    }
}
```

## 4. Beans & ApplicationContext
- Bean: Object managed by the Spring IoC container.

- ApplicationContext: Central interface for accessing beans and configuration.

```
@Component
public class CourseService {
    public String getCourseInfo() {
        return "Course: Spring Boot Basics";
    }
}

@SpringBootApplication
public class App {
    public static void main(String[] args) {
        ApplicationContext context = SpringApplication.run(App.class, args);
        CourseService courseService = context.getBean(CourseService.class);
        System.out.println(courseService.getCourseInfo());
    }
}
```

## 5. Bean Lifecycle
- Stages:

    1. Instantiation

    2. Dependency Injection

    3. Initialization (@PostConstruct)

    4. Usage

    5. Destruction (@PreDestroy)

```
@Component
public class LifecycleBean {

    @PostConstruct
    public void init() {
        System.out.println("Bean initialized!");
    }

    @PreDestroy
    public void destroy() {
        System.out.println("Bean destroyed!");
    }
}
```

## 6. Annotations
- @Component / @Service: Marks a class as a Spring-managed bean.

- @Configuration: Defines configuration classes.

- @Bean: Declares a bean inside a configuration class.


```
@Component
public class GroupService {
    public String getGroupInfo() {
        return "Group 5 - Members: 1. Hana, 2. Minh, 3. An";
    }
}

@Configuration
public class AppConfig {
    @Bean
    public GroupService groupService() {
        return new GroupService();
    }
}
```

