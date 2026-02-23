---
tags:
  - API
author:
  - jacgit18
  - chatgpt
Purpose: This is a medium article that discuss basic API design
Status: Done
Started: 
EditDate: 2024-02-25
Relates: 
Peer Reviewed: 0
dg-publish:
---


![](https://miro.medium.com/v2/resize:fit:700/1*vWvkkgG6uvgmJT8GkId98A.png)

In this deep dive, we’ll go through the API design, starting from the basics and advancing towards the best practices that define exceptional APIs.

As a developer, you’re likely familiar with many of these concepts, but I’ll provide a detailed explanation to deepen your understanding.

## API Design: An E-commerce Example

Let’s consider an API for an e-commerce platform like [Shopify](https://www.shopify.com/), which, if you’re not familiar with is a well-known e-commerce platform that allows businesses to set up online stores.

In API design, we’re concerned with defining the **inputs** (like product details for a new product) and **outputs** (like the information returned when someone queries a product) of an API.

![](https://miro.medium.com/v2/resize:fit:700/1*YfXHE565TbNOddUH-dPZfA.png)

This means that we focus on the **interface** rather than the low-level implementation

## API Design and CRUD:

So, the focus is mainly on defining how the CRUD operations are exposed to the user or system interacting with your e-commerce API.

**CRUD** Stands for Create, Read, Update, Delete. These are the basic operations of any data-driven application.

![](https://miro.medium.com/v2/resize:fit:700/1*KenCKbhOXaS8AklzmdKC0w.png)

For example, to add a new product (Create), you would make a POST request to `/api/products` where the product details are sent in the request body.

To retrieve products (Read), you need to fetch data with a GET request from `/products`.

For updating product information (Update), we use PUT or PATCH requests to `/products/:id`, where id is the id of a product we need to update.

Removing is similar to updating; we make a DELETE request to `/products/:id` where id is the product we need to remove (Delete).

## Communication Protocol and Data Transport Mechanism

Another part is to decide on the Communication Protocol that will be used, like HTTP, WebSockets, etc, and the Data Transport Mechanism: JSON, XML, or Protocol Buffers.

This is the case with RESTful APIs, but we also have GraphQL or gRPC paradigms

## API Paradigms

APIs come in different paradigms, each with its own set of protocols and standards.

## REST (Representational State Transfer)

**Pros:** Stateless: Each request from a client to a server must contain all the information needed to understand and complete the request. Uses standard HTTP methods (GET, POST, PUT, DELETE). Easily consumable by different clients (browsers, mobile apps).

**Cons:** This can lead to over-fetching or under-fetching of data- because More endpoints may be required to access specific data.

**Features:** Supports pagination, filtering (`**limit**`, `**offset**`), and sorting. Uses JSON for data exchange.

## GraphQL

**Pros:** Allows clients to request exactly what they need, avoiding over-fetching and under-fetching. Strongly typed schema-based queries.

**Cons:** Complex queries can impact server performance. All requests are sent as POST requests.

**Features:** Typically responds with HTTP 200 status code, even in case of errors, with error details in the response body.

## gRPC (Google Remote Procedure Call)

**Pros:** Built on HTTP/2, it provides advanced features like multiplexing and server push. Uses Protocol Buffers, a language-neutral, platform-neutral, extensible way of serializing structured data. Efficient in terms of bandwidth and resources, especially suitable for microservices.

**Cons:** Less human-readable compared to JSON. Requires HTTP/2 support.

**Features:** Supports data streaming and bi-directional communication. Ideal for server-to-server communication.

## Relationships in API Design

In an e-commerce setting, you might have relationships like the **user to orders**, **orders to products**, etc.

![](https://miro.medium.com/v2/resize:fit:700/1*QTDjfqDZjm6TVLaC1TFxzg.png)

Designing endpoints to reflect these relationships is important. For example, in this scenario `**GET /users/{userId}/orders**` should fetch orders for a specific user.

## Queries, Limit, and Idempotence of GET Requests

Common queries also include `**limit**` and `**offset**` for pagination or `**startDate**` and `**endDate**` for filtering products within a certain date range. This allows users to retrieve specific sets of data without overwhelming the system or the user with too much information at once.

![](https://miro.medium.com/v2/resize:fit:700/1*DH_mhd_OGwbm2vMbCa1nYA.png)

A well-designed GET request is **idempotent**, meaning calling it multiple times doesn’t change the result.

GET requests should never mutate data. They are meant only for retrieval.

## Backward Compatibility and Versioning:

When modifying endpoints, it’s important to maintain backward compatibility. This means ensuring that changes don’t break existing clients.

**Versioning**: Introducing versions (like `**/v2/products**`) is a common practice to handle significant changes.

![](https://miro.medium.com/v2/resize:fit:700/1*52t5RTNxI9Zz8sAu7Tl5xQ.png)

In the case of GraphQL, adding new fields (v2 fields) without removing old ones helps in evolving the API without breaking existing clients.

## Rate Limitations and CORS

Another best practice is to set rate limitations. This is used to control the number of requests a user can make in a certain timeframe. This is crucial for maintaining the reliability and availability of your API. It also prevents the API from DDoS attacks.

![](https://miro.medium.com/v2/resize:fit:700/1*0ZMTYW79GrOrBo86jxijjw.png)

Common practice is to also set CORS settings Cross-Origin Resource Sharing (CORS) settings are important for web security. They control which domains can access your API, preventing unwanted cross-site interactions.

## Next

API Design is just one part of a system design interview. If you’d like to learn more about the other concepts, I recommend you check out these [System Design Concepts](https://medium.com/gitconnected/6-system-design-interview-concepts-1b1882506766) next.