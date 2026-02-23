---
tags:
  - devops
  - versionControl
  - cloud
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses what are deployment artifacts.
Status: Done
Started: 
EditDate: 2024-02-22
Relates: 
Peer Reviewed: 0
dg-publish:
---
In the realm of deployment, the inclusion or separation of admin code and processes within versioned artifacts—such as container images or deployable packages—may vary based on deployment strategies and the desired level of isolation.

Deployment artifacts serve as meticulously packaged and versioned components of an application, primed for deployment in a target environment. These artifacts encapsulate everything from code and configurations to dependencies, ensuring the completeness required for seamless application execution. Formed during the build process, deployment artifacts underpin consistent and reproducible deployments.

Various types of deployment artifacts cater to diverse application landscapes:

1. **Binary Executables**: Compiled languages like C++, Rust, or Go may have deployment artifacts represented by binary executables.

2. **JAR/WAR/EAR Files**: Java applications often adopt JAR, WAR, or EAR files, bundling compiled bytecode, resources, and configuration.

3. **Docker Images**: Docker containers offer a comprehensive deployment artifact, encompassing the application, runtime, libraries, and essential components.

4. **Package Managers**: Languages like Python, Node.js, or Ruby rely on language-specific package managers (pip, npm, gem) for managing deployment artifacts.

5. **Compressed Archives**: ZIP or TAR archives are common, containing application code, configuration files, and necessary assets.

6. **Virtual Machine Images**: Some artifacts include virtual machine images (VMDK, VHD), encapsulating the entire environment needed for application execution.

7. **Cloud-Specific Formats**: Cloud platforms introduce specialized formats like AWS Lambda deployment packages or Google Cloud Function ZIP files.

8. **Compiled Assets**: Web applications may feature deployment artifacts comprising compiled assets such as CSS files, JavaScript bundles, and static HTML files.

Crucial to maintaining consistency across environments, deployment artifacts play a pivotal role in avoiding discrepancies in dependencies or configurations. Employing versioned and packaged artifacts, automated deployment pipelines seamlessly deploy applications across various environments, leveraging continuous integration and continuous deployment (CI/CD) practices.