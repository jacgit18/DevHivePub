---
tags:
  - javascript
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Async vs Defer how JavaScript is loaded
Status: Refinement
Started: 
EditDate: 2024-02-09
Relates: 
Peer Reviewed: 0
dg-publish:
---
When working with script tags in HTML, it's essential to consider various attributes for optimal performance and functionality. Here are some best practices:

#### 1. **Positioning and Defer Attribute:**
   - **Position at the Bottom:**
     - Typically, it's recommended to place script tags at the bottom of the HTML document, just before the closing `</body>` tag. This ensures that HTML content is rendered before scripts are executed.

   - **Defer Attribute:**
     - Use the `defer` attribute to indicate that the script should be executed after the document has been parsed but before the `DOMContentLoaded` event. This allows parallel loading without blocking parsing.

   - Example:
     ```html
     <script defer src="your-script.js"></script>
     ```

#### 2. **Async Attribute:**
   - **For Parallel Loading:**
     - If parallel loading is crucial and the order of execution doesn't matter, you can use the `async` attribute. This allows the script to be fetched and executed asynchronously.

   - Example:
     ```html
     <script async src="your-script.js"></script>
     ```

#### 3. **Crossorigin Attribute:**
   - **Error Logging for Cross-Origin Scripts:**
     - Include the `crossorigin` attribute for scripts that might not pass standard CORS checks. This facilitates error logging for scripts hosted on separate domains.

   - Example:
     ```html
     <script crossorigin="anonymous" src="your-script.js"></script>
     ```

#### 4. **Integrity Attribute:**
   - **Ensure Script Integrity:**
     - Use the `integrity` attribute to include inline metadata for the browser to verify that the fetched resource has not been manipulated unexpectedly. This enhances security.

   - Example:
     ```html
     <script integrity="your-hash-value" src="your-script.js"></script>
     ```

#### 5. **Nomodule Attribute:**
   - **Fallback for ES2015 Modules:**
     - Include the `nomodule` attribute to indicate that the script should not be executed in browsers that support ES2015 modules. This is useful for serving fallback scripts to older browsers.

   - Example:
     ```html
     <script nomodule src="fallback-script.js"></script>
     ```

#### 6. **Referrer Policy:**
   - **Control Referrer Information:**
     - Use the `referrerpolicy` attribute to indicate which referrer information should be sent when fetching the script or resources fetched by the script.

   - Example:
     ```html
     <script referrerpolicy="no-referrer" src="your-script.js"></script>
     ```

-   **no-referrer:** The Referer header will not be sent. 

-   **no-referrer-when-downgrade:** The Referer header will not be sent to origins without TLS (HTTPS). 

-   **origin:** The sent referrer will be limited to the origin of the referring page: its scheme, host, and port. 

-   **origin-when-cross-origin:** The referrer sent to other origins will be limited to the scheme, the host, and the port. Navigations on the same origin will still include the path. 

-   **same-origin:** A referrer will be sent for same origin, but cross-origin requests will contain no referrer information. 

-   **strict-origin:** Only send the origin of the document as the referrer when the protocol security level stays the same (HTTPS→HTTPS), but don't send it to a less secure destination (HTTPS→HTTP). 

-   **strict-origin-when-cross-origin (default):** Send a full URL when performing a same-origin request, only send the origin when the protocol security level stays the same (HTTPS→HTTPS), and send no header to a less secure destination (HTTPS→HTTP). 

-   **unsafe-url:** The referrer will include the origin and the path (but not the fragment, password, or username). This value is unsafe, because it leaks origins and paths from TLS-protected resources to insecure origins. 

#### 7. **Type Attribute:**
   - **Omit for JavaScript:**
     - Omit the `type` attribute for JavaScript scripts, as it is not required. The HTML5 specification encourages authors to omit it, and modern browsers will treat it as JavaScript by default.

   - Example:
     ```html
     <script src="your-script.js"></script>
     ```

   - **Module Scripts:**
     - If you are using JavaScript modules, use the `type="module"` attribute.

     - Example:
       ```html
       <script type="module" src="your-module-script.js"></script>
       ```



#### 8. **Nonce Attribute:**
   - **Enhance Security with Nonce:**
     - Use the `nonce` attribute with a unique value for scripts when implementing a Content-Security-Policy. This enhances security by allowing only scripts with the correct nonce value.

   - Example:
     ```html
     <script nonce="your-unique-nonce" src="your-script.js"></script>
     ```

#### 9. **Src Attribute:**
   - **Specify External Script Source:**
     - Always specify the `src` attribute with the URI of an external script. This is crucial for linking to the external script file.

   - Example:
     ```html
     <script src="your-script.js"></script>
     ```

These best practices help optimize script loading, enhance security, and ensure compatibility across different browsers. Choose attributes based on your specific requirements for script behavior and performance.