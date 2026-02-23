---
tags:
  - principles
  - MicroCodebaseDecision
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses proper naming conventions.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Camel Case.png]]
Be cognizant of naming convention  

like for a method that check truth value name it with the word "IS" at the beginning and a proper name like "isFunctionName"   

Think about where would this type of problem solution be applied to in real world to come up with a name or some other arbitrary name based on the scenario you come up with put things into context so you can understand and draw a image to establish better names




## Database Schema Naming
>[!important]
>Database schemas are useful long after you've created them and will be viewed by many other people. So good documentation is essential. Document your database schema design with explicit instructions and write comment lines for scripts, triggers, and other commands.  

- Define and use appropriate naming conventions to make your database schema designs more effective. While you may decide on a particular style or adhere to an ISO standard, the most important thing is to be consistent in your name fields. 

- Try not to use reserved words in table names, column names, fields, etc. that will likely deliver a syntax error. 

- Don’t use hyphens, quotes, spaces, or special characters. They will either require additional work or not be valid. 

- Use singular nouns, not plural nouns, for table names (for example, use StudentName instead of StudentNames). A table represents a collection, so there’s no need to make the title plural.  

- Omit unnecessary verbiage for table names (for example, use Department instead of DepartmentList or TableDepartments) 


## case

Pascal Casing - capitalizes each word:  
  
ThisShouldBePascalCase  
  
Camel Casing - is similiar to pascal case but the first word is not capitalized:  
  
thisShouldBeCamelCase



- Choose descriptive and unambiguous names.
- Make meaningful distinction.
- Use pronounceable names.
- Use searchable names.
- Replace magic numbers with named constants.
- Avoid encodings. Don't append prefixes or type information.

 beyond names, however. I also look at whether an object or method is doing more than one thing. If it’s an object, it probably needs to be broken into two or more objects. If it’s a method, I will always use the Extract Method refactoring on it,

Closure methods naming convention the outer function should include something like a gate in the name and the inner function should be something with the name of the door  


 
He says that beautiful code  makes the language look like it was made for the problem! So it’s   our  responsibility to make the language look simple! Language bigots everywhere, beware! It is not the language that makes programs appear simple. It is the programmer that make the language appear simple!


 
You get the drift. Indeed, the ratio of time spent reading vs. writing is well over 10:1. 
We are  constantly reading old code as part of the effort to write new code. 
Because this ratio is so high, we want the reading of code to be easy, even if it makes the writing harder. Of course there’s no way to write code without reading it, so  making it easy to read actually makes it easier to write. 

There is no escape from this logic. You cannot write code if you cannot read the surrounding code. The code you are trying to write today will be hard or easy to write depending on how hard or easy the surrounding code is to read. So if you want to go fast, if you want to get done quickly, if you want your code to be easy to write, make it easy to read.



These are sometimes a special case for encodings. For example, say you are building an ABSTRACT FACTORY for the creation of shapes. This factory will be an interface and will be implemented by a concrete class. What should you name them? IShapeFactory and ShapeFactory? I prefer to leave interfaces unadorned. The preceding I, so common in today’s legacy wads, is a distraction at best and too much information at worst. I don’t want my users knowing that I’m handing them an interface. I just want them to know that it’s a ShapeFactory. So if I must encode either the interface or the implementation, I choose the implementation. Calling it ShapeFactoryImp, or even the hideous CShapeFactory, is preferable to encoding the interface.


Class Names
Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in the name of a class. A class name should not be a verb. 


Method Names
Methods should have verb or verb phrase names like postPayment, deletePage, or save.

 
Use Solution Domain Names
Remember that the people who read your code will be programmers. So go ahead and use computer science (CS) terms, algorithm names, pattern names, math terms, and so forth. It is not wise to draw every name from the problem domain because we don’t want our coworkers to have to run back and forth to the customer asking what every name means when they already know the concept by a different name. 



Use Problem Domain Names
When there is no “programmer-eese” for what you’re doing, use the name from the problem domain. At least the programmer who maintains your code can ask a domain expert what it means. 

Separating solution and problem domain concepts is part of the job of a good programmer and designer. The code that has more to do with problem domain concepts should have names drawn from the problem domain.





In domain-driven design, when naming events or creating classes around events, it is advisable to use the past tense. For instance, you might name events like "AppointmentCreated" or "AppointmentConfirmed." Here's an example in TypeScript:

```typescript
// Event class for appointment creation
class AppointmentCreated {
    constructor(public appointmentId: string, public details: string) {}
}

// Event class for appointment confirmation
class AppointmentConfirmed {
    constructor(public appointmentId: string, public confirmationDate: Date) {}
}

// Example usage
const newAppointmentEvent = new AppointmentCreated("123", "Meeting with client");
const confirmedAppointmentEvent = new AppointmentConfirmed("123", new Date());

// Further actions with these events...
```

Using past tense in event naming helps convey that the event represents something that has already occurred in the domain.




# File, Function, and Variable Names 

React components should always use PascalCase, and are the only files that use PascalCase (first letter uppercase). All other files should use camelCase (first letter lowercase). Stick with .js, we don't use .jsx. 

ReactComponent.js 

functionFile.js 

While there are probably exceptions, function and variable names will also follow the above rule. If a function or variable name refers to a react component, it will use PascalCase, otherwise use camelCase. 

If you need to define a constant, like the environment variables, it should use uppercase snake_case, eg: UPPERCASE_SNAKE_CASE. 

# Acronyms 

In PascalCase and snakeCase, acronyms should generally only have the first letter capitalized: 

RgbCode, UrlEndpoint 

# Avoid Abbreviations 

no args => yes arguments 

here are times where abbreviations can make sense. Using i and/or l in a for loop for example  

for (let i = 0, l = array.length; i < l; i++) {} 



Absolutely, giving meaningful names to functions, variables, and errors is crucial for code readability, maintainability, and debugging. Here's a refined and expanded explanation:  
  
When writing JavaScript code, it's essential to avoid using anonymous functions and instead give them meaningful names. This practice improves code readability and aids in debugging, especially when encountering errors.  
  
Consider this scenario: you encounter an error in your code and check the stack trace to identify the issue. If you've used anonymous functions extensively, the stack trace will display a series of `<anonymous>` or similar placeholders, making it challenging to pinpoint the source of the error. This lack of clarity can significantly impede your debugging process.  
  
By giving your functions descriptive names, you provide valuable context within the stack trace. Instead of seeing generic placeholders, you'll see meaningful function names, making it easier to trace the error back to its source.  
  
Similarly, it's crucial to name your errors appropriately. In JavaScript, and coding in general, errors often occur during runtime. When throwing or catching errors, assigning meaningful names to them helps convey the nature of the problem.  
  
For example, instead of throwing a generic `Error` object, you could throw a more descriptive error like `InvalidInputError` or `FileReadError`. When catching errors, you can then handle them more effectively based on their specific types.  
  
Here's an example of how to name functions and errors in JavaScript:  
  
```javascript  
// Define a named function instead of an anonymous one  
function calculateTotalPrice(itemPrice, quantity) {  
return itemPrice * quantity;  
}  
  
// Usage of the named function  
const totalPrice = calculateTotalPrice(20, 5);  
  
// Throwing a named error  
function validateInput(input) {  
if (!input) {  
throw new Error('InvalidInputError: Input cannot be empty');  
}  
// Additional validation logic  
}  
  
// Example of catching and handling the named error  
try {  
validateInput(null);  
} catch (error) {  
if (error instanceof Error && error.message.startsWith('InvalidInputError')) {  
console.error('Invalid input detected:', error.message);  
// Handle the error appropriately  
} else {  
// Handle other types of errors  
console.error('An unexpected error occurred:', error);  
}  
}  
```  
  
By following these practices of naming functions and errors, you enhance the readability, maintainability, and debuggability of your JavaScript code, ultimately leading to a more robust and efficient development process.