---
tags:
  - web
  - HTTP
  - protocol
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses network request and request structure.
Status: Refinement
Started: 
EditDate: 2024-01-30
Relates: 
Peer Reviewed: 0
dg-publish: true
---
![[Http Request Method.gif]]

The process of navigating to a website involves a request from the application layer, which may traverse the transport and session layers before reaching the DNS.

Upon a request, the application connects to a DNS recursive resolver, which queries a DNS root nameserver. This root server aids in translating human-readable host names into IP addresses, directing the resolver to a Top-Level Domain (TLD) like .COM for further resolution.

The TLD server then searches for the IP address of the domain's nameserver (e.g., example.com), acting as a dictionary for translation. If the authoritative nameserver has the requested record, it returns the IP address to the DNS Recursor.

For detailed information, refer to [Cloudflare's DNS explanation](https://www.cloudflare.com/learning/dns/what-is-dns/).

Regarding HTTP requests, the process includes the CRUD method, path component, and HTTP version in the request's first line. Headers follow, and finally, the message body, appropriate for specific request methods.

HTTP Request can be resolved(accepted) or rejected and you may create test case to handle and control flow of your data/code. 

Message bodies can be single-resource or multiple-resource, distinguished by headers like Content-Type and Content-Length. Request.redirect property defines the redirect handling mode with values like follow, error, or manual.

Debugging involves using `res.text`, and HTTP rules dictate proper usage of methods like [[GET]], [[POST]], HEAD,  [[PUT]], [[PATCH]]  [[DELETE]],  and [[Other Methods]],  emphasizing adherence to design principles and avoiding misuse.

The client sends CRUD requests, receives responses, and handles data in variables. Requests can be resolved or rejected, with test cases used to control data/code flow.

The HEAD method is similar to GET but excludes the message-body in the response, useful for obtaining metadata without transferring the entity-body. The response to a HEAD request may be [cacheable](https://developer.mozilla.org/en-US/docs/Glossary/cacheable), updating cached entities based on field values like Content-Length or ETag. HEAD is also [[Idempotent]].

## HTTP Rules

Rule: GET and POST must not be used to tunnel other request methods 

Rule: HEAD should be used to retrieve response headers 

Rule: PUT must be used to update mutable resources 

Rule: POST must be used to execute controllers 

Tunneling refers to any abuse of HTTP that masks or misrepresents a message’s intent and undermines the protocol’s transparency. A REST API must not compromise its design by misusing HTTP’s request methods in an effort to accommodate clients with limited HTTP vocabulary. Always make proper use of the HTTP methods as specified by the rules in this section.

## HTTP Request Structure
![[Request Structure.png]]

The `fetch()` method is used to make network requests, resolving to a `Response` object once the server responds with headers. It defaults to a GET request but can be configured for other methods like POST. The promise does not reject on HTTP errors; you need to check `Response.ok` or `Response.status` in a `then()` handler.

Custom settings can be provided through the optional `init` object, including method, headers, body, mode, credentials, cache, redirect, referrer, referrer-policy, integrity, keepalive, and signal. For handling redirects, options like "follow," "error," and "manual" are available.

Check the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/API/fetch) for more details, including exceptions and additional information on the `fetch()` method. Additionally, [FormData](https://developer.mozilla.org/en-US/docs/Web/API/FormData) can be used to construct a set of key/value pairs representing form fields and their values for easy submission.