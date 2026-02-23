---
tags:
  - coupling
  - cohesion
  - ClassStructure
  - microservices
  - bestPractices
  - SoftwareDesign
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Coupling vs Cohesion.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish: false
---
### Coupling (Glasses vs Surgery) vs Cohesion (Master of None / Master of Specific Things)

The objective is to achieve Loose Coupling and High Cohesion.

**Coupling and Cohesion Overview:**

Coupling pertains to the inter-dependencies between modules or classes.

## Tight Coupling

In the context of human vision, tight coupling resembles the eyes. Repairing vision through surgery, akin to an eye transplant, is costly and involves significant risk. However, introducing a feature loosely connected to the body allows for easier modifications—similar to using glasses.

## Loose Coupling

Glasses offer loose coupling as they can be easily replaced without affecting the underlying vision. Changing glasses alters how we perceive the world with minimal risk and effortless maintainability.

In the realm of software, microservices should embody loose coupling. This ensures they are not tightly dependent on one another, facilitating scalability and deployment ease.

For instance, if one microservice encounters issues, others should continue functioning seamlessly. The diagram below illustrates the distinction between tightly coupled and loosely coupled [[Microservices VS Monolithic Architecture |Microservices]]:


![[coupling.jpg]]

While coupling deals with the dependencies between modules or classes, cohesion focuses on the relatedness of functions within a single module or class.

## Example of Low Cohesion:

```plaintext
---------------------------
|         Staff          |
---------------------------
| checkEmail()          |
| sendEmail()           |
| emailValidate()       |
| PrintLetter()         |
---------------------------
```

In this low cohesion example, the functions within the "Staff" module seem disparate and lack a clear thematic connection.

## Example of High Cohesion:

```plaintext
-----------------------------------------
|             Staff                      |
-----------------------------------------
| -salary                               |
| -emailAddr                            |
-----------------------------------------
| setSalary(newSalary)                   |
| getSalary()                            |
| setEmailAddr(newEmail)                 |
| getEmailAddr()                         |
-----------------------------------------
```

Contrastingly, the highly cohesive "Staff" module exhibits functions closely related to salary and email address operations. This design fosters a clear thematic unity within the module.

For a deeper exploration of these concepts, you can refer to this informative [video](https://www.youtube.com/watch?v=TCMGU7-Ir_k&list=WL&index=15&ab_channel=QuiCap).
