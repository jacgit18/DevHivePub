---
tags:
  - web
  - security
  - HTML
  - Markup
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Inner Html and its risk.
Status: Done
Started: 
EditDate: 2024-02-26
Relates: 
Peer Reviewed: 0
dg-publish: false
---
`innerHTML` is a property in JavaScript that allows you to access or modify the HTML content within an element. While it can be convenient, using it poses security risks, as it can inadvertently execute scripts and expose your application to cross-site scripting (XSS) attacks. It's recommended to use safer alternatives like `textContent` or DOM manipulation methods to avoid potential security vulnerabilities.

Here's a simple example to illustrate the potential security risk of using `innerHTML`:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>InnerHTML Example</title>
</head>
<body>

    <div id="myElement"></div>

    <script>
        // Unsafe usage of innerHTML
        document.getElementById('myElement').innerHTML = '<script>alert("XSS Attack!");</script>';
    </script>

</body>
</html>
```

In this example, setting `innerHTML` directly allows an attacker to inject a script, resulting in an alert box. To mitigate this, it's better to use safer alternatives like `textContent` or create elements using the DOM manipulation methods.


### Cross-Site Scripting (XSS) 
XSS is a security vulnerability that occurs when an application includes untrusted data in a web page without proper validation or escaping. When dealing with `innerHTML`, XSS can be a significant concern if user input is not properly sanitized.

Consider the following example:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>XSS Example</title>
</head>
<body>

    <div id="content"></div>

    <script>
        // Simulating user input from an untrusted source
        var userInput = '<img src="invalid-image" onerror="alert(\'XSS Attack!\');">';
        
        // Unsafe usage of innerHTML
        document.getElementById('content').innerHTML = userInput;
    </script>

</body>
</html>
```

In this example, a user input string containing an image tag is directly assigned to the `innerHTML` property. If an attacker provides the input, they could inject a script (in this case, an alert), leading to a potential XSS attack.

To mitigate XSS attacks, it's essential to properly sanitize user input and avoid using `innerHTML` for untrusted content. Instead, use methods like `textContent` or DOM manipulation to ensure that user input is treated as plain text rather than HTML, reducing the risk of script injection. Always validate and sanitize user input on the server side as well to ensure a more robust defense against XSS vulnerabilities.