---
tags:
  - OOP
  - instance
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses class instances.
Status: Refinement
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
In Java, a class instance represents an object created from a class blueprint. Here's a brief overview of the topics you mentioned:

1. **Class Instances:**
   - An instance is an occurrence of a class and is created using the `new` keyword.
   - Example: `MyClass obj = new MyClass();`

2. **Type References:**
   - The type reference is the class itself. Example: 
```java

public class BankAccount {
    private String accountNumber;

    public BankAccount(String accountNumber) {
        this.accountNumber = accountNumber;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acct = new BankAccount("1234");
        doWork(acct);
    }

    // The `<?>` part is a wildcard that denotes an unknown type.
    // returns void meaning no value
    static void doWork(Object obj) {
        Class<?> c = obj.getClass();
        showName(c);
    }

    static void showName(Class<?> theClass) {
        System.out.println("Class Name: " + theClass.getName());
        System.out.println("Simple Name: " + theClass.getSimpleName());
    }
}
```

- Since these methods are called from the `main` method (which is static), they need to be static as well.
- When a method is declared as [[static Keyword |static]], it can be called on the class itself rather than on an instance of the class. This is why you can call `doWork(acct)` even though `acct` is an instance variable.
- In summary, the use of `static` in this context is due to the fact that the methods (`main`, `doWork`, and `showName`) are being called from a static context (the `main` method) and, therefore, need to be static themselves. If you were to create an instance of the `Main` class and call these methods on that instance, you might consider removing the `static` modifier from these methods.

3. **Instances from String Name or Type Literal:**
   - You can create instances dynamically using reflections.

4. **Accessing Superclass and Interface:**
   - Use `getSuperclass()` and `getInterfaces()` methods in `Class` to access superclass and interface information.

5. **Retrieving Type Access Modifiers:**
   - Use `getModifiers()` method along with `Modifier` class to retrieve access modifiers.
6. **Accessing Method Information:**
   - Use `getDeclaredMethods()` to get all methods, then iterate to access details.

7. **Excluding Object Class Methods:**
   - When iterating through methods, filter out those from `Object` class.

## Wrapper Class
  - A class that encapsulates primitive data types into objects
  - Some classes and data structures can only handle objects
## Not runnable for reference only
[Runnable code](https://github.com/jacgit18/ClassAdvancedPractice)

```java
import java.lang.reflect.Field;
import java.lang.reflect.Method;
import java.lang.reflect.Modifier;


// Different ways to obtain a `Class` object in Java
public class ClassExample {

	private int privateField;

    public void publicMethod() {
        System.out.println("Executing public method");
    }

    private void privateMethod() {
        System.out.println("Executing private method");
    }


    public static void main(String[] args) {
       
        try {
        // Reflection using string name
            Class<?> c = Class.forName("com.jwhh.finance.BankAccount");
            Object instance = c.getDeclaredConstructor().newInstance();
```
3. `Object instance = c;`

   This line creates a variable `instance` of type `Object` and assigns the `BankAccount` instance (`c`) to it. This is an example of polymorphism, where you can assign an object of a subclass (`BankAccount`) to a variable of the superclass type (`Object`).

```java

            // Direct access using type literal
            Class<?> a = BankAccount.class;
            Class<?> b = instance.getClass(); // alternative way

			int modifiers = b.getModifiers();
	        System.out.println("Modifiers: " + Modifier.toString(modifiers));

            showDetails(a);

            // Direct access with class specification of literal
            Class<BankAccount> d = BankAccount.class;
            showDetails(d);

        } catch (ClassNotFoundException e) {
            e.printStackTrace();
        }
    }
```

1. `Class<BankAccount> d = BankAccount.class;`

   This line creates a variable `d` of type `Class<BankAccount>`. It represents the class object associated with the `BankAccount` class. It's often used in scenarios where you want to work with the class itself, perhaps for reflection or other advanced use cases.

2. `BankAccount d = new BankAccount('1234');`

   This line creates an instance of the `BankAccount` class and assigns it to a variable `d`. It involves instantiation, and now `d` is an object of type `BankAccount`. You've also provided a constructor argument (`'1234'`) when creating the `BankAccount` instance.

```java

    static void showDetails(Class<?> theClass) {
        System.out.println("Class Name with package: " + theClass.getName());
        System.out.println("Simple Name: " + theClass.getSimpleName());

        // Display superclass information
        Class<?> superClass = theClass.getSuperclass();
        if (superClass != null) {
            System.out.println("Superclass Name with package: " + superClass.getName());
        }

        // Display interface information
        Class<?>[] interfaces = theClass.getInterfaces();
        if (interfaces.length > 0) {
            System.out.println("Implemented Interfaces:");
            for (Class<?> interfaceClass : interfaces) {
                System.out.println("- " + interfaceClass.getName());
            }
        }

        System.out.println(); // Add a blank line for better output separation

        // Display details about fields
        Field[] fields = theClass.getDeclaredFields();
        System.out.println("Fields:");
        for (Field field : fields) {
            int modifiers = field.getModifiers();
            System.out.println("- " + Modifier.toString(modifiers) + " " + field.getName());
        }

        System.out.println(); // Add a blank line for better output separation

        // Display details about methods
        Method[] methods = theClass.getDeclaredMethods();
        System.out.println("Methods:");
        for (Method method : methods) {
            int modifiers = method.getModifiers();
            System.out.println("- " + Modifier.toString(modifiers) + " " + method.getName());
        }


        System.out.println(); // Add a blank line for better output separation

// Excluding Object class methods
for (Method method : methods) {
            if(!method.getDeclaringClass().equals(Object.class)) {
            
    System.out.println("Method: " + method.getName());

// Accessing method access modifiers
    int methodModifiers = method.getModifiers();
     
System.out.println("Modifiers: " + Modifier.toString(methodModifiers));

    // Accessing method parameters
Class<?>[] parameterTypes = method.getParameterTypes();
                
System.out.println("   Parameters: " + Arrays.toString(parameterTypes));

    // Accessing return type
Class<?> returnType = method.getReturnType();

System.out.println("   Return Type: " + returnType.getSimpleName());

    // Invoking methods
    if (Modifier.isPublic(methodModifiers)) {
    method.invoke(instance); // Invoke only public methods
      }

      System.out.println("------");
            }

    }




    static class BankAccount implements SomeInterface {
        private int accountBalance;
        public void deposit(int amount) {
            this.accountBalance += amount;
        }

        // Example inner class
    }

    interface SomeInterface {
        // Example interface
    }
}
```


8. **Method Access with Reflection:**
   - Use `getMethod()` or `getDeclaredMethod()` to obtain a specific method by name.

```java
import java.lang.reflect.Method;

public class MyClass {
    public int getId() {
        return 42;
    }

    public static void main(String[] args) {
        try {
            // Get the Class object for MyClass
            Class<?> theClass = Class.forName("fully.qualified.package.MyClass");

            // Get the Method object for the method named "getId"
            Method getIdMethod = theClass.getMethod("getId");

            // Now you can invoke the method on an instance of the class
            MyClass instance = new MyClass();
            Object result = getIdMethod.invoke(instance);

            System.out.println("Result of getId method: " + result);
        } catch (ClassNotFoundException | NoSuchMethodException | java.lang.reflect.InvocationTargetException |
                IllegalAccessException e) {
            e.printStackTrace();
        }
    }
}
```


Remember to handle exceptions like `ClassNotFoundException`, `InstantiationException`, `IllegalAccessException`, and others that may arise during reflection operations. Additionally, be cautious about performance implications when using reflection extensively, as it may incur overhead.


## Runtime class of an object

In Java, `Class<?>` is a generic type where `Class` is a non-generic class representing the runtime class of an object. The `<?>` part is a wildcard that denotes an unknown type. Here's a breakdown:

- **`Class`**: This is a class in Java's reflection package (`java.lang.reflect`) that represents the metadata about a class during runtime. It provides methods to inspect the properties of a class, such as its name, superclass, interfaces, methods, fields, etc.

- **`<?>` (Wildcard)**: The question mark represents an unknown type. In the context of generics, it's a wildcard that can match any type. Using `<?>` with `Class` means that the specific type of the `Class` object is not known at compile time.

Putting them together, `Class<?>` means a `Class` object of an unknown type. This is often used in scenarios where you want to work with the metadata of a class without specifying the exact type.

For example:

```java
Class<?> unknownClass = SomeClass.class;
```

Here, `unknownClass` is a `Class` object representing `SomeClass`, but the exact type of `SomeClass` is not specified.

It's important to note that while `Class<?>` is a common and flexible way to work with class metadata, you can also use more specific types if you know the type at compile time. For instance, `Class<T>` where `T` is the specific type.

```java
Class<String> stringClass = String.class;
```

```TypeScript
let myNumber: number = 42; 
let typeOfMyNumber: typeof myNumber; // This is a type literal
```

This restricts the `Class` object to represent only the `String` class.



