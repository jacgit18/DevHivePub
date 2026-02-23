---
tags:
  - enum
  - metaData
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses uses enums and annotation.
Status: Done
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Enums in Java are used to define a fixed set of constants. An enum type is a special type of class that represents a group of related constants. Enums provide a way to create a collection of predefined values that can be used as options or choices in your program.


```java
enum LicenseType {
    CAR,
    MOTORCYCLE,
    TRUCK
}
```

## Annotations
Annotations in Java provide a way to add metadata or extra information to your code. They can be applied to classes, methods, variables, and other program elements. Annotations do not define constants like enums; instead, they are used to provide additional information or instructions to the compiler, runtime, or other tools.

>[!note] 
>Annotations are a special kind of interface which acts as meta data while not changing target behavior but must be interpreted. 
```java
@interface LicenseInfo {
    String category();
    String issuedBy();
}
```

Now, we can apply the `@LicenseInfo` annotation to each enum constant in the `LicenseType` enum, providing specific information about the license category and the authority that issued the license.

```java
@LicenseInfo(category = "Car License", issuedBy = "Department of Motor Vehicles")
CAR,

@LicenseInfo(category = "Motorcycle License", issuedBy = "Department of Motor Vehicles")
MOTORCYCLE,

@LicenseInfo(category = "Truck License", issuedBy = "Department of Transportation")
TRUCK
```

In this example, the `category` field represents the type of license, such as a car license, motorcycle license, or truck license. The `issuedBy` field represents the authority responsible for issuing the license, such as the Department of Motor Vehicles or the Department of Transportation.







