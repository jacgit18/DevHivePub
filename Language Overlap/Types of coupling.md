---
tags:
  - data
  - ClassStructure
  - coupling
  - modularity
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses types of coupling in software development.
Status: Refinement
Started: 
EditDate: 2024-03-06
Relates: "[[Coupling vs Cohesion]]"
Peer Reviewed: 0
dg-publish:
---
Coupling measures the degree of interdependence between software modules; lower coupling is generally preferred as it indicates less dependency and higher modularity. Here's an outline from less to more tightly coupled scenarios:

### 1. **Data Coupling**(Best)
- **Description**: Functions share data through parameters, emphasizing direct and clear communication with consistent data interpretation.

### 2. **Routine Call Coupling**
- **Description**: One function calls another without passing any data. This is a basic level of coupling inherent in most software designs.

### 3. **Stamp Coupling**
- **Description**: A form of data coupling where a composite data structure (e.g., an object or struct) is passed between modules, requiring them to understand its structure.

### 4. **Type-use Coupling**
- **Description**: One module defines a data type that another module uses, either as a member data type or through function calls.

### 5. **Import Coupling**
- **Description**: A module uses definitions from another module, such as when libraries are imported. Relies on external modules but can lead to dependency issues.

### 6. **External Coupling**
- **Description**: Occurs when modules interact with external systems or hardware, linking module functionality to external processes or data structures.

### 7. **Control Coupling**
- **Description**: One module controls the flow of another by passing information on what to do (e.g., a flag or control variable), introducing dependencies on decision-making logic.

### 8. **Common Coupling**
- **Description**: Multiple modules share access to the same global data, leading to high inter-module dependency and potential for side-effects across the system.

### 9. **Content Coupling**(Worst)
- **Description**: The highest and least desirable form of coupling, where one module directly affects the internal workings of another, such as modifying private data.

## Summary

The goal in software design is often to minimize coupling where possible, striving for lower levels like data or routine call coupling and avoiding higher levels like common or content coupling. Lower coupling enhances modularity, making the software easier to understand, maintain, and extend.