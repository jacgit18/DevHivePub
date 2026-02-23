---
tags:
  - CapitalOne
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
# High-Level Design (HLD) vs. Low-Level Design (LLD) in Software Engineering

In software engineering, **High-Level Design (HLD)** and **Low-Level Design (LLD)** are two stages of system design that focus on different levels of abstraction.

---

## **High-Level Design (HLD)**

### **Focus:**

Architectural design of the system.

### **Scope:**

Defines major components, their relationships, and how data flows between them.

### **Abstraction:**

More conceptual, focusing on the big picture.

### **Includes:**

- System architecture (e.g., **microservices vs. monolith**)
- Component interactions and API design
- Data flow and high-level database schema
- Technology stack decisions

### **Analogy:**

Like a **city map** showing major roads and districts.

---

## **Low-Level Design (LLD)**

### **Focus:**

Detailed design of individual components and modules.

### **Scope:**

Defines the internal logic, data structures, and algorithms within each component.

### **Abstraction:**

More concrete, focusing on implementation details.

### **Includes:**

- Class diagrams, function signatures, and data models
- Detailed database schema with tables and indexes
- Algorithm selection and optimization
- Pseudocode or actual code structure

### **Analogy:**

Like a **blueprint of a specific building** in a city, detailing rooms, wiring, and plumbing.

---

## **Key Differences**

|Aspect|High-Level Design (HLD)|Low-Level Design (LLD)|
|---|---|---|
|**Focus**|Architecture & system structure|Component-level implementation details|
|**Scope**|Defines system modules & interactions|Defines internal logic of each module|
|**Abstraction**|Conceptual (big picture)|Concrete (granular details)|
|**Includes**|System architecture, APIs, data flow|Class diagrams, database schema, algorithms|
|**Analogy**|City map|Building blueprint|

Both HLD and LLD are **crucial**:

- **HLD** ensures the system is **scalable** and **well-structured**.
- **LLD** ensures the system is **efficient** and **maintainable** at a granular level.