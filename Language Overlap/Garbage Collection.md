---
tags:
  - languageOverlap
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses garbage collection
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[goodbye-im-out.gif]]
Making memory free is the process of garbage collection 

In JavaScript you don't need to allocate memory because it's a high level language 

So when it comes to garbage collection memory allocation and releasing is automatic and is known as automatic memory management in JavaScript 

But this process typically is associated with data types that aren't primitive like objects arrays etc where it has a reference to the memory 

So for example let's say you have an object call fruit with a name property with a value of Orange if you are real sign that fruit object to null then name property is overridden because it was in the object and isn't reachable anymore since it has no reference  

All modern browsers have a mark and sweep algorithm that clears out that data that has no reference essentially

## Memory Management

- **Garbage Collection:** JavaScript, being garbage collected, automatically manages memory. Objects become eligible for garbage collection when nothing references them.
- **Low-Level Languages:** In low-level languages, manual memory management is required, and you have to delete unreferenced items, which can lead to potential memory issues.
- **Benefits of Manual Memory Management:** While manual memory management can be challenging, it allows for high efficiency in certain situations.




# Java 

## Memory Managment 

Memory management is a central aspect in software development. Applications regularly create new objects, and objects regularly go out of scope and are no longer capable of being referenced. Let's take a look at what this means with a code snippet: 

```Java
class HelloWorld{
String message;
printHelloMessage(String name){

message ="Hello "+name;//New String instance "message" createdprint(message);

}
	//reference to message is lost once scope leaves method} 
```
In the above example, message is assigned a reference value, a "hello" message, at the start of printHelloMessage() . Once scope leaves printHelloMessage(), the reference value assigned to message is no longer reachable, but still exists in memory. Everytime printHelloMessage() is executed, a new reference value is assigned to message and allocated memory. If a process does not exist to remove these references from memory, eventually the application might run out of memory, as all available memory is being consumed by dead references. 

In languages like C and C++, removing a reference would be handled manually (e.x. by calling free or delete). This removes the reference from memory allowing the memory to be reclaimed by the system for reuse. 

Manual memory management does have some advantages. Developers have precise control over when an object is removed. Manual memory management might also be more efficient as no background process is running, consuming system resources monitoring memory usage. Though this advantage is less significant as modern automated memory systems have have improved in performance. 

However manual memory management comes with some significant downsides. With manual memory management, developers have to be conciously aware of how an application is using memory. This can be a time consuming and difficult, requiring developers to add control code for the safe allocation and deallocations of objects from memory. This code could also be distracting to other developers looking at the code, or the same developer later returning some code they have written, as it obscures the business meaningful work the code is attempting to accomplish. A developer might also fail to properly handle error conditions, which might result in objects not being deleted, leading to a memory leak. 

The considerable effort involved in manual memory management and computers rapidly becoming more powerful saw a transition to automated memory management. Today most modern programming languages, including Java, handle memory management automatically with a garbage collector. 

## Memory Management in Java 

Within Java, memory management is handled by a garbage collector, which is part of the Java Virtual Machine (JVM). Within the JVM a garbage collector is a background process that monitors objects in memory. Periodically the garbage collector will run a garbage collection which checks if objects in memory are still reachable, remove objects that are not reachable, and reorganize the objects that are still alive to make more efficent usage of memory and improve future garbage collections. 

Garbage collectors considerably reduces the amount of time and effort developers must spend managing memory. Often developers do not need to consiciously consider memory management. Garbage collection also helps to vastly reduce, though not eliminate, issues like memory leaks. 

We will take a deeper look at how garbage collectors behave in Java in the next section. 

## Garbage Collection in Java 

In the previous section we learned that Java uses a garbage collector for memory managment. But how does a garbage collector actually work? We will take a closer look at that in this section. 

### Types of Generational Garbage Collectors 

Within the HotSpot JVM, the Garbage Collector isn't a single unified concept, but has multiple implementations. Which garbage collector implementation to use will depend upon the hardware resources available and the performance requirements of your application. 

-   Serial Garbage Collector - Performs all garbage collection on a single thread. Has higher pause times, but lower resource usage. Best used on systems with only a single processor. 
    
-   Parallel Garbage Collector - Similar to the serial garbage collector, but reduces pause times by performing work using multiple threads. 
    
-   Concurrent Mark Sweep (CMS) Garbage Collector (Deprecated in JDK 9, Removed in JDK 14) - Reduces garbage collection pause times by having background process that traces objects usage while application runs. 
    
-   Garbage First (G1) Garbage Collector (Default since JDK 9) - Improves upon and replaces the CMS GC. G1 is ideally suited for multi-processor machines with access to large amounts of memory. 
    
-   Z GC (Experimental in JDK 11, Production in JDK 15) - Ultra-low latency GC that can also be scaled for application with multi-terabyte heaps. The internal implementation and behavior of GC is distinctly different from the other garbage collectors listed, and a description of it's behaviopr will be handled in a separate article. 
    

## Heap Memory 

Heap memory is an allocation of memory that is controlled by the JVM. The size of heap available to the JVM is primarily controlled with the 

```html
<mark style="background: #FFF3A3A6;">`-Xms<value> and -Xmx<value>`</mark> 
```

JVM args, setting initial heap size and max heap size respectively. 

When any thread in the JVM creates an object, they are stored in the heap. For this reason objects stored in heap are not thread safe. This is in contrast to local variables which are allocated in 
[stack memory](https://www.baeldung.com/java-stack-heap#stack-memory-in-java),  which is thread safe, and automatically cleared when the stack leaves scope. 

If heap memory becomes full it will cause the JVM to throw java.lang.OutOfMemoryError exceptions, when the JVM attempts to allocate space for new objects. For most implementations of garbage collectors in Java, heap memory is divided into multiple regions based on the "age" of an object. The number and types of regions will vary depending on the specific implementation of the garbage collector. 

## Generational Garbage Collection 

Most garbage collectors in Java are implemented as generational garbage collectors (every garbage collector except Z GC). The idea behind a generational garbage collector is that most objects are short lived, and need to be removed soon after creation. Alternatively as an object increases in age, it becomes less and less likely to become a candidate for removal. Generational garbage collectors divide the heap into multiple regions, with new objects in a more frequently checked young region and long-lived objects in a less frequently checked old region. 

By dividing the heap into multiple regions this reduces system pause time associated with garbage collections, improving throughput and responsiveness of applications running on the JVM. Garbage collectors can be further tuned to favor specific characteristics; throughput, responsiveness, resource usage, and so on, depending upon the needs of the application. 

### Heap Regions 

As mentioned earlier, the memory heap in generational garbage collectors is divided into multiple regions. Let's look at these regions in more detail. 

-   Young Region - The Young Region, as the name suggests, is the heap region that contains recently created objects. The Young Region is itself subdivided into more regions. 
    
    -   Eden Space - On initial creation, and object is stored in the Eden region of the heap until its first garbage collection. 
        
    -   Survivor Spaces - Objects that have surived being garbage collected are promoted to a survivor region. Generational collectors have multiple survivor regions, the purpose to improve garbage collector efficency. During a garbage collection, still referenced object in an Eden space or an occupied survivor space or copied or moved to an empty survivor space. 
        
-   Old Region - If an object gains enough "age", by surviving garbage collections, it will be promoted to the old region. 
    
-   Permanent/Metaspace Region - The final region is the permanent or metaspace region. Objects stored in here are typically JVM metadata, core system classes, and other data that typically exist for near the entire duration of the JVM life. Objects stored in this region are checked by the garbage collector, often only when the heap has reached a critical consumed memory threshold. 
    

## Garbage Collection Process 

At a high level, a garbage collection has three phases; mark, sweep, and compaction. Each of these steps have distinct responsibilities. Though note that dependening on the garbage collector implementation, there might be additional sub-phases within each phase that are not covered here. 

### Mark 

On object creation, every object is given, by the VM, a 1 bit marking value, initially set to false (0). This value is used by the garbage collector to mark if an object is reachable. At the start of a garbage collection, the garbage collector traverses the object graph and marks any object it can reach as true (1). 

The garbage collector doesn't scan each object individually, but insteads starts from "root" objects. Examples of root objects are; local variabes, static class fields, active Java threads, and JNI references. The below animation visualizes what the object mark phase looks like: 

![[Object Scanning.gif]]

## Sweep 

During the sweep phase all objects that are unreachable, those whose marking bit currently false (0), are removed. 

# Compaction 

The final phase of a garbage collection is the compaction phase. Live objects in the eden region or an occupied survivor region are moved and/or copied to an empty survivor region. If an object in a survivor region has gained enough tenureship, it is moved or copied to an old region. 

## Garbage Collection Pause 

During a garbage collection there might be periods where some, or even all, processing within the JVM is paused, these are called Stop-the-World Events. As mentioned in the introduction of the Heap Memory section, objects stored in heap memory are not thread safe. This in turn means that during a garbage collection, part, or all, of the JVM must be paused for a period while the garbage collector works to prevent errors from occuring as objects are checked for usage, deleted, and moved or copied. 

Tools like JDK Flight Recorder (JFR) and Visual VM can be used to monitor the frequency and duration of pauses occuring from garbage collection. How to tune a garbage collector is outside the scope of this tutorial, but monitoring garbage collector behavior, and subseqently tuning it through JVM arguments, can be key way to improve the performance of an application. 

# Types of Garbage Collections 

Just like there are different regions of heap memory, there are also different types of garbage collections. 

-   Minor - Minor garbage collections only scan the Young Regions of heap memory. Minor garbage collections occur very frequently and often have very low pause times associated with them. 
    
-   Major - Major garbage collections scan both the Young and Old regions of heap memory. Major garbage collections occur much less frequently than minor garbage collections, often being triggered by specific conditions within the VM, for example when a threshold of heap memory has been used. Significantly longer pause times are assoicated with major garbage collections as a much larger portion of the heap is being scanned. 
    
-   Full - A full garbage collection is when the entire heap is scanned, Young, Old, and Permanent/Metaspace regions. Like major garbage collections, full garbage collections are often conditions based, for example when a very high percentage of heap memory is being consumed, or being performed manually be a system administrator. Also like major garbage collections, very long pause times are associated with full garbage collections. 
    

The below animation visualizes what a garbage collection looks like: 

![[Visual Garbage Collection.gif]]

![[gc-process.gif]]