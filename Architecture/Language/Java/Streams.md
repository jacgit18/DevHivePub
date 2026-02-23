---
tags:
  - streams
  - Java
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses streams.
Status: Refinement
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[streamline.png]]
A stream is an ordered sequence of data in Java, serving as a common I/O model that abstracts the details of the underlying source or destination. Streams facilitate iteration in Java and can be categorized into two types: Byte streams, which interact with binary data (e.g., 01101110), and Text streams. Despite their distinct data representations, the general interaction remains the same for both stream types. Streams are unidirectional, meaning you either read from or write to a stream, providing a versatile mechanism for handling input and output operations.

#todo/Low/Dev 
- [ ] https://medium.com/java-content-hub/7-tricks-of-java-streams-4bc3c33a2f46

![[Read & Write Streams.png]]

![[Stream Classes.png]]

![[Reader Classes.png]]

![[Reading one Byte.png]]

![[Writing Byte.png]]


![[Reading one Character.png]]

![[Writing one Character.png]]

![[RAB.png]]

![[RAC.png]]

There are several types of stream operations in Java, including:

1.  Intermediate operations: They process the data elements in a stream and return a new stream. Example: filter, map, flatMap, sorted, etc.
2.  Terminal operations: They produce a result from a stream and don’t return another stream. Example: forEach, count, min, max, reduce, etc.
3.  Short-circuiting operations: They return as soon as a result is produced, and don’t process the rest of the elements. Example: findFirst, findAny, anyMatch, allMatch, noneMatch, etc.
4.  Stateful operations: They process the data elements in a non-linear, stateful manner and may produce different results for the same input. Example: distinct, peek, etc.
5.  Collecting operations: They collect elements from a stream into a container such as a list, set, map, etc. Example: collect, toArray, toList, toSet, toMap, etc.

![[clean.png]]

![[Chain stream.png]]

![[Accessing files.png]]

![[Buff Streams.jpg]]

![[Buff Streams code.jpg]]

![[Buff Streams line Break.jpg]]

![[Writing line Break.jpg]]

![[Reading line.jpg]]

![[Chaining Streams.jpg]]

![[Path.jpg]]

![[Read all.jpg]]

![[Buff Reader.jpg]]

![[nio package.jpg]]