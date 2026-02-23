---
tags:
  - exception
  - languageOverlap
  - errorHandling
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses exception handling.
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Exception handling stands as a cornerstone in software development, serving as a shield against unforeseen events or errors that could derail a program's normal execution. These events might arise from invalid inputs, hardware glitches, network disturbances, or simple programming oversights.

The paramount importance of exception handling manifests when errors have the potential to crash a program or introduce unpredictable behavior, risking data loss and undesirable outcomes. Through systematic and controlled exception handling, developers can proactively manage errors, ensuring the program remains stable and predictable.

In its essence, exception handling comes into play when a program encounters an error or an extraordinary condition that goes beyond the usual program flow. This involves capturing the error, identifying its root cause, and implementing appropriate measures for recovery or a graceful program exit.

Ever stumbled upon perplexing errors like IOException or IllegalNullPointer in your Java applications? These are instances of [Exceptions](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Exception.html), often termed "exceptional events," capable of disrupting the regular program flow. It's crucial to discern exceptions from errors; exceptions represent recoverable events, whereas errors demand significant code modifications due to their severity. Although the Java Development Kit (JDK) caters to general cases, Java permits developers to create custom exceptions, a practice viewed with caution within the development community.

**The Call Stack:**

Understanding the mechanism:
1. When an error arises in a method, an exception object is created, holding details about the error.
2. The runtime system traverses the call stack, searching for an exception handler—a method with code to manage the exception.
3. Once a matching handler is found, the exception object is passed to it, a process known as catching the exception.
4. If no suitable handler is found, the runtime system terminates, leading to the application's termination.

**Benefits of Exception Handling:**

- **Separation from Regular Code:** Keeps the primary program logic separate from code dealing with exceptional events.
- **Error Propagation:** Facilitates passing errors to the appropriate method.
- **Grouping and Differentiation:** Enables categorizing specific exceptions (e.g., FileNotFoundException), combining exceptions (e.g., IOException), or a catch-all by handling the Exception class.

**Types of Exceptions:**

Two categories exist: Checked and Unchecked.

- **Checked Exceptions:** Handleable at compile time. The catch or specify requirement applies, meaning the exception can be managed or propagated up the class stack using the `throw` keyword. All exceptions, except subclasses of RuntimeException or Error, fall into this category. An example is FileNotFoundException.

*For example:*
```java
package tech.strategio.tau.eclipse

import java.io.file
import java.io.IOException

public class ExceptionHandeling{
	public static void main(String args[]){
		createNewFile();
	}
	
	public static void createNewFile(){
		File file = new File("resources/nonexist.txt");
		try {
		file.createNewFile();
		} catch (IOException e) {
		System.out.println("dir doesnt exist")
		e.printStackTrace();
		}
	}	

}
```

Results
![[Exception Result.png]]

- Unchecked exceptions are not anticipated. They do not follow the catch or specify requirements. They have automatically propagated up the call stack until an appropriate exception handler is found; otherwise, the runtime terminates. 
- RuntimeException or Error are unchecked exceptions. NullPointerException is an example of an unchecked exception.

## Catching and Handling Exceptions

Catching and handling exceptions consist of three blocks: [try](https://docs.oracle.com/javase/tutorial/essential/exceptions/try.html), [catch](https://docs.oracle.com/javase/tutorial/essential/exceptions/catch.html), and [finally](https://docs.oracle.com/javase/tutorial/essential/exceptions/finally.html) blocks.  Try and catch are paired together, and finally.

- try contains statements where errors occurred. It is ALWAYS followed by a catch block, a finally block, or both.
- catch contains statements about where to handle the exceptions. A single try block can have multiple catch blocks. If consolidating exceptions into one catch block, be sure to separate exceptions with a pipe (|).
- finally is optional, and any statements in here are executed after completing the try-catch blocks. It gets called no matter what. It is good to use if you have resources that need to be closed.
- Instead of using finally(), an option to use [the try-with-resources](https://docs.oracle.com/javase/tutorial/essential/exceptions/tryResourceClose.html) statement can be used. the try-with-resources statement is a try statement that declares one or more resources. the try-with-resources statement will close each declared resource at the end of the statement.

## Throwing Exceptions

The keyword throw is used to propagate an exception to the appropriate handler.  The keyword throws can specifically throw any checked exception in the method signature or user-defined exception.

For example, rather than this method handling any exceptions, it throws the catchall Exception. If the developer wanted to throw specifically FileNotFoundException, it would change Exception to FileNotFoundException.

```java
package tech.strategio.tau.eclipse

import java.io.file
import java.io.IOException

public class ExceptionHandelingThrow{
	public static void main(String args[]){
		numbersExceptionHandling();
	}
	
 public static void createNewFileThrow() throw Exception{
		File file = new File("resources/nonexist.txt");

		file.createNewFile();
		
	}	

}
```


### Types of Errors:
Besides error constructors, JavaScript also has other core Error constructors.

-   [AggregateError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/AggregateError)
-   [EvalError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/EvalError)
-   [InternalError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/InternalError)
-   [RangeError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RangeError)
-   [ReferenceError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/ReferenceError)
-   [SyntaxError](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/SyntaxError)


### Utilizing error objects
When a runtime error occurs, a new Error object is created and thrown. With this Error object, we can determine the type of the Error and handle it according to its type.


```typescript
class CustomError extends Error {
    constructor(message: string) {
        super(message);
        this.name = "CustomError";
    }
}

function exampleFunction(value: number): string {
    try {
        if (value < 0) {
            throw new CustomError("Value must be non-negative");
        }

        // Your regular logic here

        return "Operation successful";
    } catch (error) {
        if (error instanceof CustomError) {
            console.error(`Custom Error: ${error.message}`);
            // Handle CustomError specifically
        } else if (error instanceof Error) {
            console.error(`Generic Error: ${error.message}`);
            // Handle other types of errors
        } else {
            console.error("Unknown error occurred");
        }

        return "Operation failed";
    }
}

// Example usage:
console.log(exampleFunction(42)); // Operation successful
console.log(exampleFunction(-5)); // Custom Error: Value must be non-negative, Operation failed
```



Common scenarios where exception handling is instrumental include:

- **Input Validation:** Ensuring user input conforms to required formats and falls within acceptable ranges is crucial. Exception handling is employed to catch and appropriately manage errors arising from invalid input.

- **File Handling:** Working with files introduces potential errors such as file not found, inadequate permissions, or corrupted data. Exception handling is employed to capture and address these issues, preventing program instability.

- **Network Communication:** Errors in network communication, stemming from failures or timeouts, are handled using exception handling. This ensures the program continues to function reliably despite network challenges.

- **Resource Management:** Dealing with system resources like memory or database connections entails potential errors such as resource exhaustion. Exception handling is employed to capture and address these errors, preventing program instability. It also plays a crucial role in guaranteeing proper resource release.

- **External Dependencies:** Interaction with external systems or services may result in errors or unexpected responses. Exception handling is used to manage these situations, maintaining the application's correct functioning.

- **Debugging:** During application development, exception handling aids in capturing and logging errors, streamlining the debugging process and facilitating issue resolution.

- **Business Logic:** Unanticipated conditions within the business logic of an application, beyond regular code flow, are handled through exception handling. This ensures the application's continued correct operation. There can also be overlap between business logic and other mentioned scenarios.

