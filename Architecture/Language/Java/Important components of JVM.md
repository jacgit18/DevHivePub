---
tags:
  - Java
  - JVM
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses the different components of JVM.
Status: Done
Started: 
EditDate: 2024-03-03
Relates: 
Peer Reviewed: 0
dg-publish:
---
1. **Class Loader:**
   - The class loader is a vital subsystem responsible for loading class files and executing three key functions: Loading, Linking, and Initialization.

2. **Method Area:**
   - The JVM Method Area stores class structures, metadata, Java method code, and the constant runtime pool.

3. **Heap:**
   - The heap is a shared memory space where objects, arrays, and instance variables are stored, accessible across multiple threads.

4. **JVM Language Stacks:**
   - JVM language stacks store local variables and partial results, with each thread having its own stack created upon thread creation.

5. **PC Registers:**
   - PC registers store the address of the currently executing Java virtual machine instruction, with each thread having a separate PC register.

6. **Native Method Stacks:**
   - Native method stacks hold instructions of native code, dependent on native libraries, and allocate memory on native heaps or other stack types.

7. **Execution Engine:**
   - The execution engine is a software type used for testing software, hardware, or complete systems. It lacks specific information about the tested product.

8. **Native Method Interface:**
   - The Native Method Interface serves as a programming framework allowing Java code in a JVM to call libraries and native applications.

9. **Native Method Libraries:**
   - Native Method Libraries are a collection of needed Native Libraries (C, C++) for the Execution Engine.

