---
tags:
  - CDN
  - systemComponent
  - distributedSystem
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Content Delivery Network.
Status: Done
Started: 
EditDate: 2024-03-06
Relates: "[[Caches]]"
Peer Reviewed: 0
dg-publish: false
---
A Content Delivery Network (CDN) is a network of dispersed servers that efficiently delivers static content like images, videos, and scripts. It can also cache dynamic content, such as HTML pages based on request attributes.

When a user accesses a website, the CDN server closest to them delivers static content, optimizing loading speed. If the CDN lacks the requested content, it fetches it from the origin, like a web server or Amazon S3. The origin returns the content, specifying a Time-to-Live (TTL) for caching. The CDN caches and serves the content until TTL expiration.

Considerations for CDN usage include cost, setting appropriate cache expiry times, handling CDN fallback during outages, and methods for invalidating files. CDNs improve performance by offloading static asset serving, reducing database loads through caching, and supporting millions of users through scalable system practices like stateless web tiers, redundancy, and multiple data centers.

In scaling systems for millions of users:
- Maintain stateless web tiers
- Incorporate redundancy at every tier
- Maximize data caching
- Support multiple data centers
- Host static assets in CDNs
- Scale the data tier through sharding
- Divide tiers into individual services
- Monitor the system and leverage automation tools.


Yes, in a sense, a CDN (Content Delivery Network) can be considered a network of web servers. However, there is a distinction in their primary functions:

- **Web Servers:** Typically concentrate on handling dynamic content, processing requests, and managing server-side logic. They may be centralized in a data center.

- **CDN:** Comprises a distributed network of servers strategically located in various geographic locations. While these servers can serve static content like web servers, the primary focus of a CDN is to optimize the delivery of content by caching and serving it from the server closest to the user, reducing latency and improving performance.

So, while both involve servers, a CDN's emphasis is on content delivery optimization through distribution, caching, and proximity to end-users.


## CDN Solutions
Several popular CDN (Content Delivery Network) services are widely used for delivering content globally with high performance and reliability. Here are some of the most popular CDN services:

1. **Cloudflare**: Cloudflare is one of the largest and most widely used CDN providers, offering a range of performance and security features. Its global network of edge servers helps accelerate website loading times, mitigate DDoS attacks, and optimize content delivery across various devices and networks.

2. **Akamai**: Akamai is one of the oldest and largest CDN providers, serving some of the world's largest companies. It offers a suite of content delivery, web performance, and security solutions designed to optimize the delivery of web content, video streaming, and other digital experiences.

3. **Amazon CloudFront**: Amazon CloudFront is a highly scalable and reliable CDN service provided by Amazon Web Services (AWS). It integrates seamlessly with other AWS services and offers low latency, high throughput, and global reach for delivering static and dynamic content, streaming media, and APIs.

4. **Fastly**: Fastly is a modern CDN designed for developers, offering real-time content delivery and edge computing capabilities. It provides granular control over caching and content delivery rules, enabling developers to optimize performance and customize content delivery based on user behavior and device characteristics.

5. **Microsoft Azure CDN**: Microsoft Azure CDN is a global content delivery network service offered by Microsoft Azure. It provides fast and reliable content delivery for websites, web applications, and media streaming, with integration with other Azure services such as Azure Blob Storage and Azure Media Services.

6. **StackPath (formerly MaxCDN)**: StackPath is a CDN provider focused on delivering secure and scalable content delivery solutions. It offers features such as real-time analytics, advanced caching options, and edge computing capabilities for optimizing content delivery and enhancing web performance.

7. **KeyCDN**: KeyCDN is a high-performance CDN provider offering low-latency content delivery across its global network of edge servers. It provides features such as HTTP/2 support, origin shield, and real-time analytics for optimizing content delivery and improving website performance.

8. **CDN77**: CDN77 is a global CDN provider offering high-performance content delivery solutions for websites, applications, and media streaming. It provides features such as instant purge, token authentication, and support for emerging technologies like HTTP/3 and Brotli compression.

These are just a few examples of popular CDN services available in the market. Each CDN provider offers its own set of features, pricing plans, and performance optimizations, so it's essential to evaluate your specific requirements and choose the CDN service that best meets your needs.