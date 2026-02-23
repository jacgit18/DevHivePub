---
tags:
  - devops
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses build automation.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: "[[Deployment Strategies]]"
Peer Reviewed: 0
dg-publish:
---
# Background 

Let’s think back on the DevOps pipeline.  One of the eight stages of the DevOps pipeline is Build.  One of the DevOps practices is Continuous Integration (CI).  Before CI can be achieved, Enterprises must first understand how to automate the software build. 

The software build converts source code files into software artifacts that the computer can run.  It is an end-to-end process that consists of version control, code analysis to ensure code quality, and compilation to turn source code into executable files that machines can read. 

Let’s revisit the tasks associated with the Build stage. Once the developer has submitted their code to the version control system and it has been merged for a new codebase, an automated build will occur. This automated build involves creating a repeatable, standardized process for compiling source code into binary code, packaging binary code, running automated tests, and updating the version control system. 

Before automated builds, software development teams would stitch together their applications in each environment.  So when the application was deployed from dev to test to prod, the configurations would be inconsistent.  This caused a slowdown in productivity due to conflicts and duplicate efforts and even halted deployments. 

# Purpose 

An Enterprise’s goal with build automation is to recreate the entire production environment based on what is in version control. To achieve this goal, Enterprises must utilize automation.  Enterprises will need to create scripts, and the configuration information should be stored in the version control system.  This should be a self-service system with no manual work required from human intervention. 

## Benefits of Build Automation 

There are several benefits Enterprises can gain by utilizing build automation.  These include: 

- Increased productivity so developers can focus on delivering more value. 
 
- Improvements in quality because issues are found and resolved faster. 
 
- Maintains a historical record for investigating issues. 
  

The aforementioned benefits lead to the ultimate benefits of saving time and money. 


## Build Automation Strategy 

Before Enterprises adopt build automation, they must first develop a strategy that will outline the following: 

- Build Automation process - understand the build process flow. Document the current process. Decide if some or all of the processes will be automated. 
 
- Determine which tools are needed. Create current and future state diagrams. Analyze if new tools need to be implemented to support the build automation. Conduct PoCs if necessary to better understand how the tools would work in your environment. 
 
- Analyze your talent skills- there might be knowledge gaps that can be filled with training or hiring new talent. 
 
- **Measure success by documenting key metrics such as:**  
    - The <b>number of features</b> indicates the number of implemented changes and maps to create business value. 

    - <b>Average build time</b>  indicates the average time to perform a build. 

    - The percentage of failed builds impacts the overall team output due to rework. 

    - <b>Change implementation lead time </b> affects the number of releases per period and overall product roadmap planning. 

    - The <b>frequency of builds </b> indicates the overall output and activity of the project. 


## Categories of Build Automation tools 

There are two categories of build automation tools:  utility and servers.  Utility tools primarily aim to generate build artifacts through compilation and dependency management.  Apache Ant, Apache Maven, and Gradle fit this category. 

Server tools are general web-based tools that execute build automation utilities on demand (user running a script or at the command line) or based on a schedule (nightly builds) or triggered by an event (on a pull request or commit in the version control system).  Server tools are classified by their level of automation. 

These are the classification levels: 

- **Makefile:**  
    - **Make-based tools:** a few examples are GNU make, make, and PVCS-make. 

    - **Non-Make-based tools:** Apache Ant, Apache Maven, and Grade can also act as servers. Other examples include Perforce Jam, Rake, Stack, and Psake. 

- **Build script(Makefile) generation tools:** a few examples include CMake, GNU Build Systems (Autotools), and Meson. 

- **Continuous Integration tools:** a few examples include CircleCI, Jenkins, GitHub, GitLab, TravisCI, and BitBucket. 

- **Configuration management tools:** a few examples include Ansible, Chef, Puppet, and Salt. 

- **Meta-build tools or package managers:** a few examples include Homebrew, Pkgsrc, and Nix. 
 
- **Other:** another example is Open Build Service. 


## Use Case 

### Google Cloud Platform (GCP) 

[GCP](https://cloud.google.com/) is a cloud service provider.  One of its services, Elasticsearch, uses Gradle to build and test acceleration technology to minimize CI build feedback cycle times.  See this [webcast](https://www.youtube.com/watch?v=ltVD87kVpEM) for more details. 

### Tinder 

[Tinder](https://tinder.com/) is a dating app for making matches globally.   The impact of Covid drove build system teams to work remotely.  Tinder leveraged Gradle’s build caching strategies to optimize the build speed of their android app.  See this [webcast](https://www.youtube.com/watch?v=WGCeHWEJQfw) for more details.