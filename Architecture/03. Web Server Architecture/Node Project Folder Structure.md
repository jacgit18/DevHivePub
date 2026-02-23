---
tags:
  - scalability
  - codebase
  - systemDesign
  - buildStage
  - testing
  - deployment
  - devops
  - FunctionTypes
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what to include in software builds also utility function.
Status: Refinement
Started: 2023-11-23
EditDate: 2024-03-23
Relates: 
Peer Reviewed: 0
dg-publish:
---
## Things to Consider in Build

Including test files or artifacts in the "build" folder is generally not recommended. The "build" folder typically contains the compiled or generated files that are used for deploying and running your application or software. Test files are typically separate from the production code and are used for testing and quality assurance purposes.  
  
It's a good practice to keep your test files separate from your production code to maintain code organization and to prevent any accidental inclusion of test files in your deployment packages. Test files are often located in a dedicated "tests" or "test" directory outside the "build" or "dist" folder to keep the distinction clear.  
  
Including test files in the "build" folder can lead to confusion and potential issues when deploying your application, so it's best to keep them separate.


## Utility Functions
The placement of your utility functions folder in a Node.js project structure depends on your project's specific requirements and your preferred organization. Both approaches have their advantages and can be valid, so you should choose the one that best suits your project's needs and maintainability.  
  
Here are considerations for both options:  
  
1. **Utility Folder Inside the `src` Folder**:  
- **Pros**:  
  - Keeps all project-related code, including utilities, within the project's main source directory.  
  - Easier to manage and maintain as it's closer to the rest of your application code.  
  - Create lib folder for utility functions that use libraries
- **Cons**:  
  - May lead to a cluttered `src` directory if you have a significant number of utility functions.  
  
Example structure:  
```  
/project-root  
/src  
/routes  
/models  
/utils  
app.js  
```  
  
2. **Utility Folder Outside of the `src` Folder**:  
- **Pros**:  
  - Separates utility functions from application-specific code, promoting a cleaner `src` directory.  
  - Allows you to reuse utility functions in multiple projects if organized properly.  
- **Cons**:  
  - Requires more configuration for module resolution and imports because utilities are outside the main source directory.  
  
Example structure:  
```  
/project-root  
/src  
/routes  
/models  
app.js  
/utils  
```  


In many projects, it's common to place utility functions in a separate folder outside of the `src` directory, especially when those utilities are meant for reuse or when you want to keep the `src` directory focused on application-specific code. You can then configure your Node.js project to recognize the utility folder as a module, making it accessible to your application code.  
  
Ultimately, the choice between these two options should be based on your project's specific needs, your team's conventions, and your preference for code organization. Just make sure to document your project's structure and any configuration changes to ensure that your team and collaborators understand how everything is organized.


## Other Folders 
The organization between "pages/" and "ui/" directories serves specific purposes and is intentionally designed. The "ui/" directory contains reusable React code such as components, hooks, and contexts, while the "pages/" directory is responsible for mapping components to routes and combining code from "ui/" and "lib/".

In general, code from "pages/" should not be dependent on (import) code from other parts of the application, except for setting up top-level routes in "src/App.js" and for parent pages on sub-pages.

The "lib/" folder is dedicated to non-UI code, including domain objects, business logic (often in the form of pure functions), and infrastructural code like network layer clients, formatting utilities, and platform communication (e.g., Browser Storage or IndexDB). Starting with "lib/" and "lib/core/" at the beginning of a project is recommended, allowing the remaining folders to evolve naturally.

The "manifest.json" file in the "public" folder is used for Progressive Web App (PWA) configurations.

Dependencies are made more explicit by adhering to certain rules:
- Code from "lib/" never imports code from "ui/" or "pages/".
- Code from "pages/" should import implementation code from "ui/" or "lib/".
- Code from "ui/" may import code from "lib/", but not from "pages/".
- Generally, code may import from within their own top-level namespace: i.e., "pages/", "lib/", "ui/".

This organization helps maintain clarity and separation of concerns within the project, facilitating easier maintenance and scalability as the project evolves.



