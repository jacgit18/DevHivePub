---
tags:
  - bestPractices
  - versionControl
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Semantic Versioning.
Status: Done
Started: 2024-02-07
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Version.jpeg]]

Semantic Versioning, often abbreviated as SemVer, is a versioning scheme designed to convey meaning about the underlying changes in software. 

1. **Initial Development Phase**
    - Begin with version **0.1.0**, signaling the early stages of development.

2. **First Stable Release**
    - Mark the transition to a stable, production-ready version with **1.0.0**.

Te Semantic versioning consists of three components: MAJOR.MINOR.PATCH.

1. **MAJOR version:** Increased for incompatible API changes. This signifies that existing code might break or not work with the new version.

2. **MINOR version:** Incremented for backward-compatible additions or enhancements. New features are added in a backward-compatible manner.[^1] [^2] [^3]

3. **PATCH version:** Incremented for backward-compatible bug fixes. This indicates that the software's functionality remains the same but has been fixed or improved.

In addition to these version numbers, SemVer allows for pre-release and build metadata:

- **Pre-release version:** Additional labels for pre-release versions, such as alpha, beta, rc (release candidate), followed by a number (e.g., 1.0.0-alpha.1).

- **Build metadata:** Additional build metadata, usually denoted with a plus sign and a series of dot-separated identifiers (e.g., 1.0.0`+build123`).

A version number follows this pattern: 
- MAJOR.MINOR.PATCH`[-PreRelease][+BuildMetadata]`
- ***v***`3.8.5-alpha+123ab`
- ***v***`3.9.0-rc.2`

The idea is that developers and systems relying on the software can quickly understand the nature of changes and decide whether to update based on the version number. Semantic Versioning promotes clarity, predictability, and a standard way of versioning software across different projects and dependencies.

[^1]: A **backward-compatible manner** means that new features or updates to a system, software, or API do not break or disrupt existing functionality. In other words, existing code, applications, or users that rely on the old version can continue to work without modification even after the update is applied.

[^2]: **Backward-Compatible Additions:** Adding a new feature, method, or parameter in a way that doesn't affect the old functionality. For instance, adding an optional parameter to a function is backward-compatible because existing code doesn't need to change.

[^3]:**Backward-Compatible Enhancements:** Improving performance or usability without changing the interface or behavior that existing systems depend on.
