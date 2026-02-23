---
tags:
  - Java
  - library
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses package, libraries, and modules.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
In the Java ecosystem, the organizational hierarchy from small to big follows the structure: Package ➔ Module ➔ Library.

**Package:**
A package serves as a namespace that organizes a group of related Java classes and interfaces. It is analogous to a folder in a computer directory system, allowing developers to organize and group classes logically. Packages help maintain order and structure in Java projects.

**Module:**
A module is a higher-level organizational unit that encompasses multiple related Java packages and their associated resources. It includes a descriptor file specifying which packages/resources are exposed, used by the module, and other relevant information. Introduced in Java 9 as part of the Java Platform Module System (JPMS), modules facilitate the packaging of Java applications or APIs as separate entities. A module is packaged as a modular JAR file and defines its dependencies on other modules.

**Library:**
A Java library is a compilation of classes created by external developers, which users can download and integrate into their projects. Libraries provide a way to expand the functionality of Java applications without reinventing the wheel. Typically, a library consists of multiple modules, each offering specific functionality. For instance, a collections library might contain modules such as List, Set, and Map. Libraries are composed of collections of .jar files, with each .jar file representing a module within the library.

In summary, while a package organizes classes within a namespace, a module groups related packages and resources with a defined structure, and a library encompasses multiple modules, providing a comprehensive collection of functionality that users can integrate into their Java projects.