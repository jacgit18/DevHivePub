---
tags:
  - Java
  - Framework
  - springBoot
  - spring
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Spring vs Spring Boot.
Status: Done
Started: 
EditDate: 2024-02-04
Relates: 
Peer Reviewed: 0
dg-publish: true
---
[Spring](https://spring.io/projects/spring-boot)  and Spring Boot are related frameworks, but they serve different purposes and have some key differences:

1. **Purpose:**
   - **Spring:** The core Spring framework provides comprehensive infrastructure support and a set of features for building enterprise applications in Java. It covers various modules such as data access, messaging, aspect-oriented programming, and more.
   - **Spring Boot:** Spring Boot, on the other hand, is specifically designed to simplify the process of building production-ready, stand-alone Spring-based applications. It focuses on convention over configuration, providing defaults for application setup, and minimizing the need for manual configuration.

2. **Configuration:**
   - **Spring:** In traditional Spring applications, developers often need to configure many aspects of the application explicitly, leading to verbose XML or Java-based configuration files.
   - **Spring Boot:** Spring Boot embraces convention over configuration, providing sensible defaults for many configurations. It aims to minimize the need for boilerplate code and manual configuration, allowing developers to get started quickly.

3. **Embedded Server:**
   - **Spring:** When using the core Spring framework for web applications, you typically need an external servlet container (like Tomcat, Jetty, or others) to deploy your application.
   - **Spring Boot:** Spring Boot includes an embedded server (e.g., Tomcat, Jetty, or Undertow) by default. This means you can package your Spring Boot application as a standalone JAR or WAR file, and it includes the necessary server components, simplifying deployment.

4. **Project Setup:**
   - **Spring:** Setting up a new Spring project may require manual configuration, adding dependencies, and setting up build files.
   - **Spring Boot:** Spring Boot provides a set of starter templates for various types of applications (web, data, messaging, etc.). These starter templates include pre-configured settings and dependencies, allowing developers to bootstrap projects quickly.

In summary, while Spring is a comprehensive framework for building enterprise applications in Java, Spring Boot is a project within the Spring ecosystem that focuses on simplifying and accelerating the development of production-ready Spring applications by providing defaults and convention-based configurations.

## Spring Boot in Depth

Spring Boot is a framework built on top of the Spring framework, designed to simplify the process of developing and deploying Java-based applications. It streamlines the configuration and development process, offering conventions over configurations and providing a set of pre-built templates.

The integration of an embedded Tomcat server in Spring Boot means that you can package your application as a standalone JAR (Java Archive) file, including the Tomcat server within it. This makes it convenient to deploy and run your web application without the need for an external application server. Spring Boot takes care of many configuration details, allowing you to focus on your application logic.

In terms of design patterns, Spring Boot encourages the use of various design patterns to enhance the modularity, maintainability, and scalability of applications. Some common design patterns promoted by Spring Boot include:

1. **Dependency Injection (DI):** Spring Boot uses DI to manage and inject dependencies, reducing tight coupling between components and improving testability.

2. **Inversion of Control (IoC):** IoC is a core concept in Spring Boot, where the control of application flow is inverted, and the framework manages the lifecycle of objects.

3. **Model-View-Controller (MVC):** Spring Boot follows the MVC pattern for building web applications, separating concerns between the model (data), view (presentation), and controller (handling user input).

4. **Factory Pattern:** Spring Boot utilizes the factory pattern for creating and managing objects, enhancing flexibility and maintainability.

5. **Observer Pattern:** Events and listeners in Spring Boot adhere to the observer pattern, enabling components to react to changes in state.

Overall, Spring Boot leverages these design patterns to provide a structured and modular approach to application development, making it easier to build robust and maintainable software.