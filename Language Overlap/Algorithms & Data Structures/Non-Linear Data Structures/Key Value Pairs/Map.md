---
tags:
  - dataStructure
  - non-linear
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses
Status: Done
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
In computer science, the term "map" refers to a data structure that stores collections of key-value pairs, where each key is unique and used to access the associated value. Maps are utilized for efficient data retrieval and manipulation based on keys and are commonly implemented using hash tables or similar data structures.

**Key Points:**

1. **Map vs. Object:** In some programming languages, the terms "map" and "object" are used interchangeably. An object, typically used in object-oriented programming, can represent key-value pairs, effectively acting as a map or dictionary.

2. **Map Variations:** The characteristics of a map may vary depending on its implementation. Some maps use hash tables and are not considered linear data structures, while others use ordered data structures, like balanced binary search trees, making them non-linear data structures. The choice depends on the specific use case and language.

## Hashmap vs. Map

In Java, a map is an interface with built-in methods, while a hashmap is a specific implementation of the map with its own set of methods. A hash table is another implementation of the map interface.

![[Map Structure.png]]

```java
Map capitalCities = new HashMap();  

HashMap<String, String> capitalCities = new HashMap<String, String>(); 
```

```typescript
const capitalCities = new Map<string, string>();

const capitalCities: Map<string, string> = new Map<string, string>();
```

**Key Points:**

- A map represents a mapping between a key and a value and is found in the `java.util` package.
- Maps are ideal for key-value association mapping, such as dictionaries, zip codes to cities, manager-employee relationships, or classes and students.
- Maps do not allow duplicate keys, but some implementations permit null keys and values. The order of a map depends on the specific implementation, with TreeMap and LinkedHashMap offering predictable orders, unlike HashMap.

![[MapHeiarchyJava.png]]

## LinkedHashMap and TreeMap

**LinkedHashMap:** This class extends HashMap and maintains the order of elements inserted, allowing access in insertion order.

```java
Map<String, Integer> map = new LinkedHashMap<>();
map.put("vishal", 10);
map.put "sachin", 30);
map.put "vaibhav", 20);
```

**TreeMap:** It is used to implement the Map interface and NavigableMap. TreeMap sorts key-value pairs according to natural ordering or a provided comparator.

```java
TreeMap<Integer, String> tree_map = new TreeMap<>();
```

[Source: [GeeksforGeeks](https://www.geeksforgeeks.org/treemap-in-java/)]

## Dictionaries vs. Maps

**Terminology:** In various programming languages, the terms "dictionary" and "map" are used to describe key-value data structures.

**Key Differences:**

1. **Terminology:** "Dictionaries" are commonly used in Python, while "maps" are more prevalent in languages like Java and C++.

2. **Data Structures:** Python dictionaries are often hash tables, whereas maps in languages like Java can be implemented using different data structures.

3. **Key Characteristics:** Python dictionaries typically have keys of immutable data types, are unordered, and keys are unique. In other languages, maps can offer more key flexibility and may or may not maintain order.

4. **Usage:** Python natively supports dictionaries, whereas Java's Map interface is standard in its library, requiring other languages to use libraries or implement their map-like data structures.

In summary, dictionaries and maps serve as key-value data structures, but specific properties and terminology vary between languages. Dictionaries are common in Python, while maps are widely used in Java and other languages with variations in their implementations.
