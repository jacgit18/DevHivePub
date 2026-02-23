---
tags:
  - testing
  - bestPractices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses type of testing techniques.
Status: Refinement
Started: 
EditDate: 2024-02-02
Relates: "[[Code Coverage]]"
Peer Reviewed: 0
dg-publish: true
---
![[Black and white box.gif]]
### **What is Software/Application testing?**

Software testing is a process to detect hidden errors, or functional inconsistencies in a software’s code by running the software through various tests. After the successful completion of testing rounds, a detailed report is prepared by the tester, which assists developers in making sure that the software runs error free, and fix all the identified issues, such as – 

-   Architectural Errors
-   Poor Designs
-   Invalid Functionality
-   Security Loopholes

Though there are various types of software testing, the widely used testing measures are considered to be Black Box Testing, White Box Testing, and Grey Box Testing. These testing measures differ majorly in their approach, yet are collectively effective in helping developers keep their code clean and functional.

![[Testing type.png]]

#### BLACK BOX TESTING

Also known as Behavioral Testing, Black box testing is a software testing technique where the application is tested without the knowledge of its internal code structure. The name only depicts that the software program is not perceived through the tester’s eyes. This type of testing commonly focuses on only the input and resultant output rather than the mechanisms that enable the output of the software system you can almost think about it as testing from the perspective of the user.

Resultant meaning occurring or produced as a result or consequence of something.

Black box involves [[Functional Testing]], [[Non-functional Testing]], & [[Pre Acceptance Testing#^84bb7e |Regression Testing]].

There are several [[Black Box in Depth |technologies]] used in black box testing due to it nature of not having access to codebase.

Some of the errors tested by this method are – 

1.  Function errors
2.  Interfacing errors
3.  Database errors
4.  Performance errors
5.  Initialization errors  

##### **Black Box Testing Techniques** 

1.  **Information Gathering –** As the first step of every security assessment procedure, information gathering involves extracting knowledge about the application from outside sources by using Search Engine Discovery/ Reconnaissance and Web App Fingerprint. 

2.  **Configuration and Deploy Management Testing –** Application Configuration management weakness are assessed in this technique, along with hunting sensitive information from the backups and old, unrefined files. 

3.  **Data Validation Testing –** This technique employs Reflected Cross-Site Scripting, Stored Cross-site Scripting and [**SQL Injections**](https://www.kratikal.com/blog/sql-injection-attack-a-major-application-security-threat/) to examine whether the provided data is valid or complete.

4.  **Cryptography –** Black Box Testing inspects the unencrypted channels through which sensitive information is sent, as well as examination of weak SSL/TLS ciphers and the protection of the application’s transport layer.

**How is Black Box Testing performed?**

The basic methodology of any Black Box Testing is as follows:

1.  Understanding specifications of the application which is to be tested with a Software Requirements Specification (SRS) document. 
2.  Evaluation of the software with a set of valid inputs to save time and get good test coverage.
3.  Test cases preparation for the maximum coverage of inputs.
4.  Running of test cases in the system to generate outputs. 
5.  Marking of the ‘Failed’ steps and sending them for fixing to the development team.
6.  Retesting of the test cases.

![[Blackbox testing.png]]

#### WHITE BOX TESTING

This type of software testing evaluates and verifies the ‘source code’, or the internal workings of a software system, such as its code and infrastructure. White Box is an essential part in a modern Continuous Integration(CI)/Continuous Delivery (CD) of automated build processes. Some of the software code of the following are tested by this method also is done from the perspective of the developer  –

1.  Internal security holes
2.  Poorly structures paths
3.  Specific input flow
4.  Expected output
5.  Conditional loop functionality

##### White Box Testing Techniques

White Box Testing typically involves surveying the application for vulnerabilities with reference to notable security standards, such as SANS Top 25 and [**OWASP Top 10 Application Security Risks**](https://www.kratikal.com/blog/android-application-hacking/). 

1.  **SANS Top 25 –** This well-known, and most frequently utilized, compilation of security vulnerabilities depicts the common errors found in all types of systems.

2.  **OWASP Top 10 –** The Open Web Application Security Project’s Top 10 illustrates the 10 common vulnerabilities found in an application, such as Injection, Broken Authentication and Session Management, Cross-site Scripting, and many more. 

**How is White Box Testing performed?**

To simplify the process of a white box test, it can be divided into two basic steps –

1.  **Understanding of the Source Code**

The fundamental of every testing process is to learn and understand the source code of an application. White box testing involves internal testing, which requires testers to have a thorough knowledge of languages used in programming of the applications they are testing. Since security is the main motive of performing a test, the tester’s awareness of secure coding practice is essential. 

The tester should be able to detect and identify security issues within an application’s code to keep the attackers from taking advantage of the vulnerabilities by injecting malicious code into the application.

2.  **Test Case Creation and Execution**

The following basic step involves testing the application’s code to review its proper flow and structure. One way to do this is by writing additional code so the application’s code can be tested. This method requires a deep technical understanding of the code, and is performed by the developer. The other method involves Manual Testing, trial and error method, and the use  of various tools for the execution of the testing procedure, such as MobSF, BurpSuite, Dex2Jar, and many more.

![[Whitebox Testing.png]]
#todo/Low/Dev 
- [ ] merge with white box notes above 
## White Box Testing Techniques

A major White box testing technique is Code Coverage analysis. Code Coverage analysis eliminates gaps in a [Test Case](https://www.guru99.com/test-case.html) suite. It identifies areas of a program that are not exercised by a set of test cases. Once gaps are identified, you create test cases to verify untested parts of the code, thereby increasing the quality of the software product

There are automated tools available to perform [Code coverage analysis](https://www.guru99.com/code-coverage.html). Below are a few coverage analysis techniques a box tester can use:

**Statement Coverage**:- This technique requires every possible statement in the code to be tested at least once during the testing process of [software engineering](https://www.guru99.com/what-is-software-engineering.html).

**Branch Coverage –** This technique checks every possible path (if-else and other conditional loops) of a software application.

Apart from above, there are numerous coverage types such as Condition Coverage, Multiple Condition Coverage, Path Coverage, Function Coverage etc. Each technique has its own merits and attempts to test (cover) all parts of software code. **Using Statement and Branch coverage you generally attain 80-90% code coverage which is sufficient.**

Following are important WhiteBox Testing Techniques:

- Statement Coverage
- Decision Coverage
- Branch Coverage
- Condition Coverage
- Multiple Condition Coverage
- Finite State Machine Coverage
- Path Coverage
- Control flow testing
- Data flow testing

## Types of White Box Testing

_White box testing_ encompasses several testing types used to evaluate the usability of an application, block of code or specific software package. There are listed below —

- **Unit Testing:** It is often the first type of testing done on an application. [Unit Testing](https://www.guru99.com/unit-testing-guide.html) is performed on each unit or block of code as it is developed. Unit Testing is essentially done by the programmer. As a software developer, you develop a few lines of code, a single function or an object and test it to make sure it works before continuing Unit Testing helps identify a majority of bugs, early in the software development lifecycle. Bugs identified in this stage are cheaper and easy to fix.
- **Testing for Memory Leaks**: Memory leaks are leading causes of slower running applications. A QA specialist who is experienced at detecting memory leaks is essential in cases where you have a slow running software application.

Apart from the above, a few testing types are part of both black box and white box testing. They are listed below

- **White Box [Penetration Testing](https://www.guru99.com/learn-penetration-testing.html):** In this testing, the tester/developer has full information of the application’s source code, detailed network information, IP addresses involved and all server information the application runs on. The aim is to attack the code from several angles to expose security threats.
- **White Box Mutation Testing**: [Mutation testing](https://www.guru99.com/mutation-testing.html) is often used to discover the best coding techniques to use for expanding a software solution.

## White Box Testing Tools

Below is a list of top white box testing tools.

- [EclEmma](https://www.eclemma.org/download.html)
- [NUnit](http://nunit.org/)
- [PyUnit](https://www.guru99.com/python-unit-testing-guide.html)
- [HTMLUnit](http://htmlunit.sourceforge.net/)
- [CppUnit](https://sourceforge.net/projects/cppunit/)

## Advantages of White Box Testing

- Code optimization by finding hidden errors.
- White box tests cases can be easily automated.
- Testing is more thorough as all code paths are usually covered.
- Testing can start early in [SDLC](https://www.guru99.com/software-development-life-cycle-tutorial.html) even if GUI is not available.

## Disadvantages of WhiteBox Testing

- White box testing can be quite complex and expensive.
- Developers who usually execute white box test cases detest it. The white box testing by developers is not detailed and can lead to production errors.
- White box testing requires professional resources with a detailed understanding of programming and implementation.
- White-box testing is time-consuming, bigger programming applications take the time to test fully.
#### **GREY BOX TESTING**

Grey Box Testing is a combination of Black Box Testing and White Box Testing techniques. In Black Box, the tester is not aware of the internal workings of the application being tested, while White Box Testing allows the tester to have that knowledge freely. Grey Box Testing grants a partial information of the internal structure to the tester, including the access to internal data and design for the purpose of creating test cases. It also is testing from the perspective of the user with access to internals. 

##### Grey Box Testing Techniques 

1.  **Identity Management Testing –** This Grey Box Testing technique evaluates Role Definitions, User Registration Process, and Account Provisioning Process to detect vulnerabilities.

2.  **Authentication Testing –** Components of the authentication process are tested, such as Default Credentials, Weak Lock Out Mechanism, the Bypass Authentication Schema and the credentials transported over an encrypted channel. 

3.  **Authorization Testing –** Through Directory Transversal File Include, Bypass Authorization Schema and [**Privilege Escalation**](https://www.kratikal.com/blog/vapt-prevent-privilege-escalation/), the Authorization Mechanism is tested to discover vulnerabilities.

4.  **Session Management Testing –** This technique Tests things like Cookie Attributes, Session Fixation and Session Hijacking to analyze the application. 

5.  **Input Validation Testing –** Through certain Injection attacks, like SQL Injection, XML Injection, SSI Injection, and Cross-site Scripting attacks, the application’s vulnerabilities are highlighted. 

**How is Grey Box Testing Performed?**

Since Grey box testing does not require a tester to design the test cases, these cases are created based on the algorithm evaluating the program’s internal conditions, behavior and structural knowledge. The tester only carries the test out and interprets the result by ensuing the following steps:

1.  Identification and selection of the inputs from Black and White box testing methods, and the verification of likely outputs from these inputs.
2.  Identifying the key paths for testing phase, and understanding sub-functions for deep-level testing.
3.  Identifying likely inputs and outputs for the, and from the, sub-functions.
4.  Executing sub-function test cases, and verifying the outcomes.

![[Grey box testing.png]]

This distinction between each type of testing comes down to  the degree of access we have into the software. In black-box testing, we're just given the software as-is and need to test it. 

With white-box testing, we have additional programmatic access to test individual functions. Then grey being in the middle of black and white testing.

When it comes to automation testing for something like black-box testing it can be much harder to automate in comparison to the other test.

#todo/Low/Dev 
- [ ] merge with grey box notes above 
## Gray Box Testing Techniques

Gray box testing techniques are designed to enable you to perform penetration testing on your applications. These techniques enable you to test for [insider threats](https://www.imperva.com/learn/application-security/insider-threats/), such as employees attempting to manipulate applications, and external users, such as attackers attempting to exploit [vulnerabilities](https://www.imperva.com/learn/application-security/cve-cvss-vulnerability/).

With gray box testing, you can ensure that applications work as expected for authenticated users. You can also verify that malicious users cannot access data or functionality you don’t want them to.

When performing gray box testing, there are several techniques you can choose from. Depending on which testing phase you are in and how the application operates, you may want to combine multiple techniques to ensure all potential issues are identified.

### Matrix Testing

Matrix testing is a technique that examines all variables in an application. In this technique, technical and business risks are defined by the developers and a list of all application variables are provided. Each variable is then assessed according to the risks it presents. You can use this technique to identify unused or un-optimized variables.

### Regression Testing

Regression testing is a technique that enables you to verify whether application changes or bug fixes have caused errors to appear in existing components. You can use it to ensure that modifications to your application are only improving the product, not relocating faults. When performing regression testing, you need to recreate your tests since inputs, outputs, and dependencies may have changed.

### Pattern Testing

Pattern testing is a technique that evaluates past defects to identify patterns that lead to defects. Ideally, these evaluations can highlight which details contributed to defects, how the defects were found, and how effective fixes were. You can then apply this information to identifying and preventing similar defects in new versions of an application or new applications with similar structures.

### Orthogonal Array Testing

Orthogonal array testing is a technique you can use when your application has only a few inputs that are too complex or large for extensive testing. This technique enables you to perform test case optimization, where the quality and number of tests performed balance test coverage with effort. This technique is systematic and uses statistics to test pair-based interactions.

## Gray Box Testing Pros and Cons

When determining whether or not to use gray box testing, you should consider the following pros and cons. These can help you determine if gray box testing is appropriate for your testing situation and how much value it may provide.

### Pros

Pros of gray box testing include:

- Clear testing goals are established, making it easier for testers and developers
- Testing accounts for a user perspective, improving the overall quality of products
- Testers do not need to have a programming expertise
- Testing methods create more time for developers to fix defects
- It can provide the benefits of both black and white box testing
- It can eliminate conflicts between developers and testers
- It is cheaper than integration testing

### Cons

Cons of gray box testing include:

- It can be difficult to associate defects with root causes in distributed systems
- Code path traversals are limited due to restricted access to internal application structure
- It does not allow for full white box testing benefits since not all internals are accessible
- It cannot be used for algorithm testing
- Test cases can be difficult to design