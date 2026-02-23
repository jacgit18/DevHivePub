---
tags:
  - compile
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what compiler is and how it woks.
Status: Done
Started: 2024-02-26
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
A compiler is a software tool that translates source code written in a high-level programming language into machine code or an intermediate code that can be executed by a computer. The purpose of a compiler is to facilitate the execution of a program by converting the human-readable code written by a programmer into a format that the computer's hardware can understand.

Here is a step-by-step breakdown of how a compiler works:

1. **Lexical Analysis (Scanning):**
   - The first phase involves breaking the source code into a sequence of tokens. Tokens are the smallest units of meaning in a programming language, such as keywords, identifiers, literals, and operators.
   - Whitespace and comments are usually removed during this phase.

2. **Syntax Analysis (Parsing):**
   - The compiler then uses a parser to analyze the structure of the code based on the grammar rules of the programming language. The result is a parse tree or an abstract syntax tree (AST), representing the hierarchical structure of the code.
   - Syntax errors are detected during this phase.

3. **Semantic Analysis:**
   - The compiler checks the semantics of the code to ensure it makes sense and adheres to the language rules beyond just syntax.
   - Type checking is performed, ensuring that variables are used in a manner consistent with their declared types.

4. **Intermediate Code Generation:**
   - The compiler generates an intermediate code that is independent of the target machine architecture. This code serves as an abstraction that simplifies the process of targeting different platforms.

5. **Code Optimization:**
   - The compiler may perform various optimizations on the intermediate code to improve the efficiency of the resulting machine code.
   - Common optimizations include constant folding, loop optimization, and dead code elimination.

6. **Code Generation:**
   - The compiler translates the optimized intermediate code into machine code specific to the target architecture.
   - Register allocation and instruction selection are key steps in this phase.

7. **Code Linking (if applicable):**
   - In some cases, the compiler may link the generated code with external libraries or modules to create a complete executable program.

8. **Output:**
   - The final output of the compilation process is an executable file or binary code that can be run on a computer.

It's important to note that this is a simplified overview, and different compilers may implement these phases in slightly different ways. Additionally, some languages may have additional steps or specific optimizations tailored to their characteristics. The compilation process is a crucial step in software development, enabling programmers to write code in a high-level language and execute it on various hardware platforms.


### Compiled programming languages
A compiled language is translated into machine code for direct execution by the processor, resulting in faster program execution.

In contrast, an interpreted language executes instructions directly without prior compilation into machine language, making interpreted programs run slower.

Compiled languages allow code execution by the CPU, while interpreted languages rely on real-time interpretation without a separate compilation step.

An example of a compiled language is C++. In C++, the source code is translated into machine code or an intermediate code by a compiler before execution, providing faster and more efficient performance. Other compiled languages include C, Java (partially compiled to bytecode), and Rust.