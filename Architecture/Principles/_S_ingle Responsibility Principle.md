---
tags:
  - SOLID
  - principles
  - ClassStructure
  - functionStructure
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses single responsibility in SOLID principles.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: 
Peer Reviewed: 0
dg-publish:
---
Single Responsibility Principle is another SOLID design principle were you should have functions, classes, or objects should have one and only one responsibility.

You don’t need to have an object that does different or many tasks. An object can have many behaviors([[Functions rules#Have No Side Effects |side effects]]) and methods, but all of them are relevant to it’s single responsibility.

So, whenever there is a change that needs to happen, there will be only one class to be modified, this class has one primary responsibility.


> _The key benefit of this principle is that it reduces coupling between the individual component of the software and Code._

For example, If you put more than one functionality in one Class in Java, it introduces **coupling** between two functionality, and even if you change one feature, there is a chance you broke coupled functionality, which requires another round of testing to avoid any surprise on the production environment.

1. **Java:**
   ```java
   // Before SRP
   class Report {
       String content;
       
       void generateReport() {
           // logic to generate report
       }
       
       void saveToFile() {
           // logic to save report to file
       }
   }
   
   // After SRP
   class Report {
       String content;
       
       void generateReport() {
           // logic to generate report
       }
   }
   
   class ReportSaver {
       void saveToFile(Report report) {
           // logic to save report to file
       }
   }
   ```

2. **Python:**
   ```python
   # Before SRP
   class Report:
       def __init__(self, content):
           self.content = content
       
       def generate_report(self):
           # logic to generate report
       
       def save_to_file(self):
           # logic to save report to file
           
   # After SRP
   class Report:
       def __init__(self, content):
           self.content = content
       
       def generate_report(self):
           # logic to generate report
           
   class ReportSaver:
       def save_to_file(self, report):
           # logic to save report to file
   ```

These examples demonstrate separating the responsibilities of generating a report and saving it to a file into distinct classes, adhering to the Single Responsibility Principle.