# Creating a Maven Application with Layered Structure

## What is a Maven Project?
- **Maven** is a build automation and project management tool for Java.
- A **Maven project** is structured with a standard directory layout (`src/main/java`, `src/test/java`, etc.) and managed by a `pom.xml` file.
- The `pom.xml` defines project metadata, dependencies, plugins, and build configurations.
- **Key Benefit:** Consistency across projects, automated dependency management, and easy integration with CI/CD pipelines.

---

## How to Create a Maven Project
- Use [Spring Initializr](https://start.spring.io/) to quickly bootstrap a Maven project.
- Steps:
  1. Go to [start.spring.io](https://start.spring.io/).
  2. Select **Project** → Maven.
  3. Choose **Language** → Java.
  4. Configure project metadata (Group, Artifact, Name, Description).
  5. Select Java version and dependencies.
  6. Click **Generate** to download the project as a `.zip`.

---

## How to Write Name and Group ID
- **Group ID:** Represents the organization or company (reverse domain style).  
  Example: `com.example` or `org.mycompany`.
- **Artifact ID (Name):** Represents the project name.  
  Example: `student-management-system`.
- **Best Practice:**  
  - Group ID = company/domain identifier.  
  - Artifact ID = specific project/module name.  
- **Example:**  
  ```xml
  <groupId>com.thiri</groupId>
  <artifactId>student-management-system</artifactId>
