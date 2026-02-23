---
tags:
  - ClassStructure
  - OOP
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Composition and Encapsulation.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---

The choice between encapsulation and composition depends on the specific design goals and requirements of your software. Encapsulation is a fundamental principle of object-oriented programming that involves bundling the data (attributes) and methods (functions) that operate on the data into a single unit, known as a class.

Composition, on the other hand, involves creating complex objects by combining simpler ones. It's a way to build relationships between classes by creating instances of one class within another.

In many cases, a combination of both encapsulation and composition is used to achieve a well-organized and maintainable design. Encapsulation helps in hiding the internal details of a class, promoting information hiding and reducing dependencies. Composition allows for flexibility by assembling classes to create more complex structures.

Ultimately, the choice depends on the specific requirements of your application. Encapsulation is more about how you structure individual classes, while composition is about how those classes interact and collaborate.

```javascript
// Encapsulation: Creating a 'Person' class with private properties using closures
class Person {
  constructor(name, age) {
    // Private properties
    let _name = name;
    let _age = age;

    // Getter methods for encapsulation
    this.getName = () => _name;
    this.getAge = () => _age;
  }

  // Public method
  introduce() {
    console.log(`Hi, I'm ${this.getName()} and I'm ${this.getAge()} years old.`);
  }
}

// Composition: Creating another class 'Job' to represent a person's job
class Job {
  constructor(title, salary) {
    this.title = title;
    this.salary = salary;
  }

  // Public method
  displayJob() {
    console.log(`I work as a ${this.title} with a salary of ${this.salary}.`);
  }
}

// Using composition and encapsulation together
class Employee {
  constructor(person, job) {
    // Composition: Instances of 'Person' and 'Job' classes
    this.person = person;
    this.job = job;
  }

  // Public method using encapsulated data
  introduceWithJob() {
    this.person.introduce();
    this.job.displayJob();
  }
}

// Example usage
const person1 = new Person('Alice', 28);
const job1 = new Job('Software Engineer', '$80,000');

const employee1 = new Employee(person1, job1);
employee1.introduceWithJob();
```

In this example:

- `Person` class encapsulates the name and age properties with private variables and provides getter methods.
- `Job` class represents a person's job with a title and salary.
- `Employee` class uses composition by having instances of `Person` and `Job` classes as its properties.
- The `Employee` class has a method `introduceWithJob` that calls methods from both the `Person` and `Job` classes to display information.


```javascript
// Encapsulation using nested functions and closures
function createPerson(name, age) {
  // Private properties
  let _name = name;
  let _age = age;

  // Nested functions with closures for encapsulation
  function getName() {
    return _name;
  }

  function getAge() {
    return _age;
  }

  // Public method
  function introduce() {
    console.log(`Hi, I'm ${getName()} and I'm ${getAge()} years old.`);
  }

  // Return an object with public methods
  return {
    introduce: introduce
  };
}

// Example usage
const person1 = createPerson('Bob', 35);
person1.introduce(); // Output: Hi, I'm Bob and I'm 35 years old.

// Attempting to access private properties directly will result in an error
// console.log(person1._name); // Error: person1._name is not defined
```


## Encapsulation
  - All data and methods are stored in an appropriate class
  - Instance variables (data) are kept private and use accessor methods (getters/setters) to control access to them
  - The separation and containerization of attributes/methods into a single data object unit.
  - Allows restricted access to members and methods of a class to only those that need it, through keywords such as private, protected, and public.