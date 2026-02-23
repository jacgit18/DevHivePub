---
tags:
  - servers
  - systemComponent
  - distributedSystem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses caches.
Status: Refinement
Started: 
EditDate: 2024-03-23
Relates: 
Peer Reviewed: 0
dg-publish:
---
![[Cache 2.jpeg]]

A cache functions as a temporary storage layer, providing faster access to frequently used data or computations compared to the original, slower storage location. It is utilized in various computing domains, such as web browsers, where it accelerates access to web pages or images during return visits, and CPUs, where it stores instructions and data near the processor, reducing program execution times. Caches aim to reduce access times and improve data retrieval speeds, thereby enhancing overall system performance. 


Caches, usually smaller and faster in access times, act as temporary storage solutions, reducing latency and alleviating the burden on servers and databases. Effective cache utilization is advisable for data that is frequently read but infrequently modified. However, critical data should be stored in persistent data stores to mitigate the risk of volatile memory loss on cache server restarts.

  
Cache implementations can vary based on the specific needs and architecture of a system. While cache servers like Redis are commonly used due to their specialized features and performance characteristics, caching can also be implemented in various other forms without using a dedicated cache server.


#todo/Med/Dev 
- [ ] [Redis Demystified: A Simple Introduction for System Design 🧩 - DEV Community](https://dev.to/priya01/redis-demystified-a-simple-introduction-for-system-design-56mb)

# Cache Types
![[cacheEveryWhere.jpeg]]
## CDN Caching
Content Delivery Networks (CDNs) also serve as caches for static content like HTML, CSS, JavaScript, images, and videos.

**Edge Caches:** Placed at strategic points in a network, storing and delivering content closer to end-users. 

## Web Server Caching
Web servers implement local caches, enabling them to retrieve and return information without reaching out to downstream servers.

**Proxy Caches:** Servers that sit between clients and origin servers, storing copies of resources to reduce server load and speed up access.  

**Browser Caches:** Local caches on user devices, storing web page elements to avoid re-downloading when revisiting a site.  

**Client-Side Caching:** Caches reside on the client-side, such as browsers, file systems, and servers acting as reverse-proxies.

  
**Session Caches:**  
- **User Session Caches:** Store user-specific data during a session, reducing the need to query a database repeatedly.  
  

## Database Caching
Databases inherently include caching mechanisms to avoid repetitive queries, enhancing performance, especially under heavy loads.

- **Query Caches:** Store the result set of database queries, reducing the need to re-run identical queries.  
- **Object Caches:** Store serialized objects or database records, improving retrieval speed.  
  

## Application Caching 
Application caching involves placing caches between applications and data stores. These caches typically store database query results and/or frequently used objects. Examples include Memcached, Redis, and DynamoDB.

## Computer Related Component Caches

**CPU Cache:**  
- **L1 Cache:** Located directly on the CPU chip, it is the smallest but fastest cache level.  
- **L2 Cache:** Slightly larger and slower than L1, it acts as a middle ground between L1 and main memory.  

**File Caches:**  
- **Operating System Caches:** Hold recently used file data in memory, speeding up access times.  
- **Network File System (NFS) Caches:** Cache data from remote file systems to reduce the need for frequent network requests.  

**In-Memory Caches:**  
- **Distributed Caches:** Spread across multiple nodes in a network, enhancing scalability and fault tolerance.  
- **Local Caches:** In-memory caches within a single machine, reducing latency for frequently accessed data.  

**Hardware Caches:**  
- **Disk Caches:** Temporary storage for recently read or written data on hard drives or SSDs, enhancing I/O performance.  

**Memory-Mapped Caches:**  
- **Memory-Mapped File Caches:** Use a portion of virtual memory to access files directly, improving I/O efficiency.  

## Consistency Challenge
One challenge with caching is ensuring data consistency between the cache and the underlying data layer (e.g., server or database).


## Cache Strategies
Different strategies exist for caching data, such as cache-aside, read-through, write-through, and write-behind. Cache-aside involves the backend application checking the cache before querying the database, fetching data from the database if not found in the cache, and storing it for future use. Read-through sees the backend application querying the cache before the database, updating the cache automatically if data is absent. Write-through simultaneously writes data to both the cache and the database, while write-behind first writes to the cache and then asynchronously to the database.

Upon a web page request, the server checks the cache for the response. If present, it promptly delivers the data to the client; otherwise, it queries the database, caches the response, and then serves it to the client—a strategy known as a read-through cache. Various caching strategies exist based on data type, size, and access patterns.

Mitigating failures: A single cache server represents a potential single point of failure(SPOF), defined in Wikipedia as follows: “A single point of failure (SPOF) is a part of a system that, if it fails, will stop the entire system from working”. As a result, multiple cache servers across different data centers are recommended to avoid SPOF. Another recommended approach is to over provision the required memory by certain percentages.This provides a buffer as the memory usage increases. 


## Cache Policies 
Various policies govern the management of cached data, including LRU (Least Recently Used), LFU (Least Frequently Used), and FIFO (First-In-First-Out). LRU evicts cached data that hasn't been accessed for the longest time when the cache is full. LFU prioritizes evicting data accessed the least frequently. FIFO removes data stored in the cache for the longest duration when capacity is reached.

Implementing an expiration policy is crucial. It ensures timely removal of expired cached data, preventing permanent storage in memory. Striking a balance in expiration dates is advised, avoiding excessively short duration's to prevent frequent database reloads and steering clear of overly long duration's to prevent stale data.

Eviction Policy:Once the cache is full, any requests to add items to the cache might cause existing items to be removed. This is called cache eviction. Least-recently-used(LRU) is the most popular cache eviction policy. Other eviction policies, such as the Least Frequently Used (LFU) or First in First Out (FIFO), can be adopted to satisfy different use cases. 


![[Cache going wrong.gif]]

![[Cache 1.jpeg]]


![[redisUseCase.jpeg]]

![[Cache Eviction Strategies.gif]]