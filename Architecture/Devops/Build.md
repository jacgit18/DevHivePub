---
tags:
  - devops
  - CapitalOne
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses software build.
Status: Done
Started: 
EditDate: 2024-11-11
Relates: 
Peer Reviewed: 0
dg-publish: true
---
In programming, a 'build' refers to a specific version of a software program, identified by a unique build number. It involves compiling source code, linking libraries, packaging assets, and creating executable software. The 'Build' encompasses the entire process of delivering your software, including steps like generating sources, compiling and testing, packaging into formats like JAR or WAR, and performing health checks. Modern practices favor full automation through tools like Maven or Ant, enabling Continuous Integration for seamless development workflows.

#### Application Build Process InDepth
1. **Source Code Generation:** Develop the source code for the software.

2. **Compilation:** Translate the source code into machine-readable code (e.g., bytecode or machine code).

3. **Testing:** Execute various tests, including unit and integration tests, to ensure the code functions as intended.

4. **Library Linking:** Connect necessary libraries and dependencies to the compiled code.

5. **Asset Packaging:** Bundle assets such as images, configuration files, or other resources with the compiled code.

6. **Executable Software Creation:** Combine all components into an executable software version.

7. **Packaging:** Package the software into specific formats like JAR (Java Archive), WAR (Web Application Archive), EJB-JAR (Enterprise JavaBeans Archive), or EAR (Enterprise Archive).

8. **Health Checks:** Run health checks using static analyzers (e.g., Checkstyle, Findbugs, PMD) to ensure code quality.

9. **Report Generation:** Generate reports detailing the results of tests and analysis.

10. **Automation:** Modern best practices advocate for full automation using build tools like Maven or Ant.

11. **Continuous Integration:** Execute the entire build process continuously to integrate changes seamlessly into the software, known as Continuous Integration.

These steps collectively constitute the comprehensive process of building and delivering software.

#### Builds in Different Environments

# Differences Between Branch-Level and PR-Level Builds in Jenkins

The difference between running a build on a branch in Jenkins and running a build at a Pull Request (PR) level lies in the scope and purpose of each build:

## 1. Branch-Level Build

- **Triggered By**: Commits or changes made directly to a specific branch (e.g., `main`, `dev`).
- **Purpose**: Ensures the branch itself remains stable and the code works as expected after changes.
- **Outcome**: Tests and builds are run on the current state of that branch, validating its stability.

## 2. PR-Level Build

- **Triggered By**: Creation or updates of a Pull Request.
- **Purpose**: Validates changes before merging into the target branch, ensuring that the PR’s changes won’t break the main or target branch.
- **Outcome**: The build runs on a combination of the PR branch and its target branch (often the main or development branch), testing how the PR changes interact with the current state of the target branch.

## Key Differences

- **Branch Build**: Tests only the branch itself with its latest commits.
- **PR Build**: Tests the combination of the source branch (where the PR originates) and the target branch (where the PR will be merged), simulating the post-merge state.

## Build Stage Skipping After a Successful Build

Build stages may be skipped after a successful build due to caching mechanisms or build optimization techniques, such as:

- **Build Caching**: Jenkins may cache results from previous successful builds, allowing it to skip unnecessary stages if no changes were detected. For instance, if Jenkins detects that no new commits or code changes impact the current build, it might skip repeating previously successful steps.
- **Declarative Pipelines**: In Jenkins declarative pipelines, you can use a `when` directive to skip stages conditionally (e.g., only running specific stages if changes occurred in certain files).
- **Build Success**: If a previous build of the same commit or PR passed, Jenkins might skip redundant steps to optimize resource usage.

## Does Stage Skipping Happen at Both Levels?

Yes, stage skipping can happen at both branch and PR levels if conditions for skipping (e.g., no relevant changes, caching, pipeline conditions) are met. The key factor is whether Jenkins detects that certain stages have already been successfully completed in a previous build or if there are no new changes requiring those stages to run again.
