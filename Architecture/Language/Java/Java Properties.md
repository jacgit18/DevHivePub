---
tags:
  - Java
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses java properties.
Status: Done
Started: 
EditDate: 2024-03-03
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Java, properties refer to a key-value pair configuration that is often used for various settings in applications. The `Properties` class in Java is a part of the `java.util` package and provides a simple way to manage configuration data. Here are key aspects of Java properties:

1. **Key-Value Pairing:**
   - Properties in Java are represented as key-value pairs, where each key is associated with a specific value. Both keys and values are strings.

2. **Properties Class:**
   - The `Properties` class is a standard Java class used to handle key-value pairs. It extends the `Hashtable` class and thus inherits its methods for manipulating the data.

3. **Loading and Storing Properties:**
   - Properties can be loaded from or stored to various sources, such as files, streams, or other `Properties` objects.
   - The `load(InputStream)` method reads properties from an input stream, and `store(OutputStream, String)` writes properties to an output stream.

4. **Example Usage:**
   - Here's a simple example of using Java properties:
     ```java
     import java.util.Properties;

     public class Example {
         public static void main(String[] args) {
             Properties properties = new Properties();

             // Setting properties
             properties.setProperty("database.url", "jdbc:mysql://localhost:3306/mydb");
             properties.setProperty("database.user", "username");
             properties.setProperty("database.password", "password");

             // Retrieving a property
             String url = properties.getProperty("database.url");
             System.out.println("Database URL: " + url);
         }
     }
     ```

5. **Common Use Cases:**
   - Configuration settings: Storing configuration parameters for an application.
   - Internationalization: Managing language-specific properties for localization.
   - Data persistence: Saving and loading application state or settings.

6. **Property File Convention:**
   - It's common to store properties in a file with a `dot.properties` extension. This file contains lines in the format `key=value`.

   Example property file (`config.properties`):
   ```properties
   database.url=jdbc:mysql://localhost:3306/mydb
   database.user=username
   database.password=password
   ```

   Usage to load properties from a file:
   ```java
   try (InputStream input = new FileInputStream("config.properties")) {
       properties.load(input);
   } catch (IOException e) {
       e.printStackTrace();
   }
   ```

Java properties are versatile and widely used in Java applications to manage configurable settings, making it easy to modify the behavior of an application without changing its source code.