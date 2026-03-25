# Step-by-Step: Create a Spring Project with Website
## 1. Install Prerequisites
- Java Development Kit (JDK): Install JDK 17 or later.

- Maven or Gradle: Build tool (Maven is most common).

- IDE:  IntelliJ IDEA, Eclipse, or VS Code.

- Spring Initializr: Tool to bootstrap Spring projects.

## 2. Create a New Spring Boot Project
### Option A: Using Spring Initializr (recommended)
- Go to https://start.spring.io.

- Fill in:

    - Project: Maven

    - Language: Java

    - Spring Boot: Latest stable version

    - Group: com.example

    - Artifact: spring-website

    - Dependencies: Spring Web, Thymeleaf

- Click Generate → Download the ZIP → Extract and open in your IDE.

### Option B: Using IDE (IntelliJ/Eclipse)
Most IDEs have a “New Spring Project” wizard that uses Spring Initializr internally.

## 3. Project Structure

- Your project will look like this:
```
spring-website/
 ├─ src/main/java/com/example/springwebsite/
 │   ├─ SpringWebsiteApplication.java
 │   ├─ controller/
 │   │   └─ HomeController.java
 │   └─ model/
 ├─ src/main/resources/
 │   ├─ templates/
 │   │   └─ index.html
 │   └─ application.properties
 └─ pom.xml
```

## 4. Create the Main Application Class

```
package com.example.springwebsite;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringWebsiteApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringWebsiteApplication.class, args);
    }
}
```

## 5. Create a Controller

```
package com.example.springwebsite.controller;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String home(Model model) {
        model.addAttribute("message", "Welcome to My Spring Website!");
        return "index"; // maps to index.html in templates
    }
}
```

## 6. Create a Web Page (Thymeleaf Template)
- Inside src/main/resources/templates/index.html:

```
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Spring Website</title>
</head>
<body>
    <h1 th:text="${message}"></h1>
    <p>This is a simple Spring Boot + Thymeleaf website.</p>
</body>
</html>
```

## 7. Configure Application Properties
- Inside src/main/resources/application.properties:

```
spring.application.name=spring-website
server.port=8080
```

## 8. Run the Application
- In your IDE, run SpringWebsiteApplication.

- Or via terminal:
```
mvn spring-boot:run
```

- Open browser: http://localhost:8080
You should see your Spring-powered website 

## 9. Extend the Website
- Add more controllers (AboutController, ContactController).

- Add more templates (about.html, contact.html).

- Use CSS/JS for styling (place in src/main/resources/static).

## 10. Deploy (Optional)

- Package with Maven:

```
mvn clean package

```
- Run JAR:

```
java -jar target/spring-website-0.0.1-SNAPSHOT.jar
```
- Deploy to server (Tomcat, AWS, Azure, etc.).