---
tags:
  - devops
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what Maven is and its history.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
### Why Maven was created

Maven was created to provide a standard way to build projects, establish a clear definition of project structure, enable easy publishing of project information, and facilitate the sharing of JARs across multiple projects.

**Pom.xml (Project Object Model) file:**

The POM file is Maven's fundamental unit of work, represented in XML format. It contains project information and configuration details essential for Maven to build the project. Maven utilizes the POM file to manage the project's lifecycle and dependencies.

**Key improvements in Maven:**

1. **Default directory structure:** Maven introduced a standard directory structure for Java projects, making it easier for developers to navigate between projects.

2. **Standardization of build process:** Maven standardized the build process by defining a default lifecycle with phases like compile, test, and package. This allows developers to build projects using a consistent approach on the Maven CLI.

3. **External storage of dependencies:** Maven shifted the practice of storing dependencies externally, moving them out of version control and into a remote repository, commonly known as Maven Central. This simplifies the process of updating dependency versions.
![[Maven Timeline.png]]

**Maven's Functionality and Extensibility:**

Maven operates within the Java Virtual Machine (JVM) and primarily builds Java applications. However, its extensibility is evident through 3rd party plugins like kotlin-maven-plugin for Kotlin projects, scala-maven-plugin for Scala projects, and similar language-specific plugins.

A Java virtual machine enables the execution of Java programs and those compiled to Java bytecode from other languages. The JVM adheres to a specification that formally outlines the requirements for JVM implementations.

**Maven Project Definition:**

Maven projects are defined using an XML build file, which includes:

- Project group, artifact ID, and version.
- Configuration of plugins to apply.
- Declaration of project dependencies.

**Command to Run Maven Wrapper on a Specific Port:**

```bash
./mvnw spring-boot:run -Dspring-boot.run.arguments=--server.port=8090
```

Once a Maven build file is created, you can interact with the project using the Maven Command Line Interface (CLI). For instance, running `mvn test` executes the default Maven lifecycle, including phases such as:

- `validate`: Ensures the Maven project is correct.
- `compile`: Transforms Java source code into bytecode.
- `test`: Executes tests to verify application functionality.

Each phase incorporates specific goals, such as the `compiler:compile` goal in the compile phase. Further understanding of phases and goals will be explored later.

**Maven as an Open Source Project:**

Maven is an open-source project available on GitHub, part of the Apache Software Foundation. It operates under a free-to-use model, supported by donations to the foundation.