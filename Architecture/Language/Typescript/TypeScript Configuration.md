---
tags:
  - typescript
author:
  - jacgit18
  - chatgpt
Purpose: This documentation explain the different aspects of ts-config file.
Status: Done
Started: 
EditDate: 2024-02-26
Relates: 
Peer Reviewed: 0
dg-publish:
---
In TypeScript's `tsconfig.json` file, the `target` and `module` options are used to configure the version of ECMAScript to which the TypeScript code will be compiled, as well as the module system used for generating code. Let's break down these concepts:  
  
### `target` Option:  
  
- **Description:** Specifies the ECMAScript version to which TypeScript will compile the code.  
- **Possible Values:**  
- `ES3`, `ES5`, `ES6/ES2015`, `ES2016`, `ES2017`, `ES2018`, `ES2019`, `ES2020`, `ESNext`  
- **Context:**  
- Determines the language features that TypeScript allows and the polyfills it includes.  
  
### `module` Option:  
  
- **Description:** Specifies the module system to use when generating JavaScript code.  
- **Possible Values:**  
- `CommonJS`, `AMD`, `System`, `UMD`, `ES6/ES2015`, `ES2015`, `ES2020`, `ESNext`, `None`  
- **Context:**  
- Affects the format of the generated JavaScript code.  
  
### Available Modules and Differences:  
  
1. **CommonJS:**  
- **Usage:** Commonly used in Node.js environments.  
- **Generated Code:** Uses `require()` and `module.exports`.  
- **Context:** Suitable for server-side applications or projects with Node.js environments.  
  
2. **AMD (Asynchronous Module Definition):**  
- **Usage:** Primarily used in browser environments, emphasizing asynchronous loading.  
- **Generated Code:** Uses `define()` and `require()`.  
- **Context:** Suitable for projects that need to load modules asynchronously in a browser.  
  
3. **System:**  
- **Usage:** Not as common.  
- **Generated Code:** Uses `System.register` for module definition.  
- **Context:** Historically used with the SystemJS module loader.  
  
4. **UMD (Universal Module Definition):**  
- **Usage:** Suitable for projects that need compatibility across various environments (browser, Node.js, AMD, CommonJS).  
- **Generated Code:** Supports multiple module systems in a single file.  
- **Context:** Provides a compromise for projects targeting both browsers and server-side environments.  
  
5. **ES6/ES2015 Modules:**  
- **Usage:** Native support in modern browsers and Node.js.  
- **Generated Code:** Uses `import` and `export` statements.  
- **Context:** Suitable for projects targeting environments that support ES6 modules.  
  
### Relationship Between `target` and `module`:  
  
- **Matching Versions:**  
- It's common and often recommended to have the `target` and `module` settings match. For example, if targeting ES6, using `module: 'ES6'` is typical.  
  
- **Differences:**  
- You can have different `target` and `module` settings, but this might lead to suboptimal or unexpected results. For instance, targeting ES6 with CommonJS modules might generate code that relies on ES6 features not available in environments that support CommonJS.  
  
- **Use Cases:**  
- Aligning `target` and `module` is generally straightforward and avoids potential compatibility issues. However, in specific scenarios (e.g., transitioning from CommonJS to ES6 modules), temporarily mismatching them might be necessary.  
  
### Example `tsconfig.json`:  
  
```json  
{  
"compilerOptions": {  
"target": "ES6",  
"module": "CommonJS",  
// ... other options  
}  
}  
```  
  
In this example, TypeScript will compile the code to ES6 and use the CommonJS module system for generating JavaScript code. Adjust these settings based on your project's requirements and the environments you are targeting.