---
tags:
  - MacroCodebaseDecision
  - CleanPrinciples
  - functionStructure
  - bestPractices
  - FunctionTypes
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Functions rules.
Status: Refinement
Started: 
EditDate: 2024-03-07
Relates: 
Peer Reviewed: 0
dg-publish:
---
- Small.
- Do one thing.
- Use descriptive names.
- Prefer fewer arguments.
- Have no side effects.
- Don't use [[Flag Arguments]]. Split method into several independent methods that can be called from the client without the flag.  flag would be some boolean value you use as a arg in a function and use it within your conditional logic 
- So, another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its implementation.


It’s hard to make a small switch statement. Even a switch statement with only two cases is larger than I’d like a single block or function to be. It’s also hard to make a switch statement that does one thing. By their nature, switch statements always do  N  things. Unfortunately we can’t always avoid switch statements, but we  can  make sure that each switch statement is buried in a low-level class and is never repeated. We do this, of course, with polymorphism.


 
## Function Arguments
The ideal number of arguments for a function is zero (niladic).  Next comes one (monadic), followed closely  by two (dyadic). Three arguments (triadic) should be avoided where possible. More than  three (polyadic) requires very special justification—and then shouldn’t be used anyway. Arguments are hard. They take a lot of conceptual power.

 
Arguments are even harder from a testing point of view. Imagine the difficulty of writing all the test cases to ensure that all the various combinations of arguments work properly. If there are no arguments, this is trivial. If there’s one argument, it’s not too hard. 
With two arguments the problem gets a bit more challenging. With more than two arguments, testing every combination of appropriate values can be daunting.


 
Arguments are even harder from a testing point of view. Imagine the difficulty of writing all the test cases to ensure that all the various combinations of arguments work properly. If there are no arguments, this is trivial. If there’s one argument, it’s not too hard. 
With two arguments the problem gets a bit more challenging. With more than two arguments, testing every combination of appropriate values can be daunting.


```java
public class OutputArgumentsExample {
    public static void main(String[] args) {
        int x = 5;
        int y = 10;

        // Pass two variables as arguments and modify them inside the function
        incrementValues(x, y);

        System.out.println("Modified values: x = " + x + ", y = " + y);
    }

    public static void incrementValues(int a, int b) {
        a += 1;
        b += 1;
    }
}
```

## Clean Code Version
```java
public class OutputArgumentsExample {
    public static void main(String[] args) {
        int x = 5;
        int y = 10;

        // Call the method and capture the returned values
        int incrementedX = incrementValue(x);
        int incrementedY = incrementValue(y);

        System.out.println("Modified values: x = " + incrementedX + ", y = " + incrementedY);
    }

    public static int incrementValue(int value) {
        return value + 1;
    }
}
```



Output arguments are harder to understand than input arguments. When we read a function, we are used to the idea of information going  in to the function through arguments and  out  through the return value. We don’t usually expect information to be going out through the arguments. So output arguments often cause us to do a double-take.

[[Monadic functions]]


## Argument Objects
When a function seems to need more than two or three arguments, it is likely that some of those arguments ought to be wrapped into a class of their own. Consider, for example, the difference between the two following declarations:

Circle makeCircle(double x, double y, double radius); 
Circle makeCircle(Point center, double radius); 

Reducing the number of arguments by creating objects out of them may seem like cheating, but it’s not. When groups of variables are passed together, the way x and y are in the example above, they are likely part of a concept that deserves a name of its own.



## Have No Side Effects
Side effects are lies. Your function promises to do one thing, but it also does other  hidden things. Sometimes it will make unexpected changes to the variables of its own class. 

Sometimes it will make them to the parameters passed into the function or to system globals. In either case they are devious and damaging mistruths that often result in strange temporal couplings and order dependencies. 

Consider, for example, the seemingly innocuous function in Listing 3-6. This function uses a standard algorithm to match a userName to a password. It returns true if they match and false if anything goes wrong. But it also has a side effect. Can you spot it?



Functions should either do something or answer something, but not both. Either your function should change the state of an object, or it should return some information about that object. Doing both often leads to confusion.



Some programmers follow Edsger Dijkstra’s rules of structured programming.14 Dijkstra said that every function, and every block within a function, should have one entry and one exit. Following these rules means that there should only be one return statement in a function, no break or continue statements in a loop, and never,  ever,  any goto statements.


While we are sympathetic to the goals and disciplines of structured programming, those rules serve little benefit when functions are very small. It is only in larger functions that such rules provide significant benefit. 

So if you keep your functions small, then the occasional multiple return, break, or continue statement does no harm and can sometimes even be more expressive than the single-entry, single-exit rule. On the other hand, goto only makes sense in large functions, so it should be avoided.