---
tags:
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses .env in different languages.
Status: Done
Started: 
EditDate: 2024-03-03
Relates: 
Peer Reviewed: 0
dg-publish:
---
Given that, among other reasons, The 12-Factor App [recommended a strict separation of config from code](https://12factor.net/config). This practice quickly took hold throughout the developer community commonly through the use of _.env_ (dotenv) files. These are plain text files that store a list of key/value pairs, defining the environment variables required for an application to work, as in the example below.


```java
package com.settermjd.twilio.envvars;

import io.github.cdimascio.dotenv.Dotenv;
import io.github.cdimascio.dotenv.DotenvException;

public class Main {
    public static void main(String[] args) {
        Dotenv dotenv = null;
        dotenv = Dotenv.configure().load();
        System.out.println(String.format(
            "Hello World. Shell is: %s. Name is: %s",
            System.getenv("SHELL"),
            dotenv.get("NAME")
        ));
    }
}
```


   ```javascript
   import dotenv from 'dotenv';
   dotenv.config();

   // Now you can access your environment variables like this:
   const apiKey = process.env.API_KEY;
   const databaseUrl = process.env.DATABASE_URL;

   // Use the variables in your application
   console.log('API Key:', apiKey);
   console.log('Database URL:', databaseUrl);
   ```
