---
tags:
  - API
  - web
  - protocol
  - processes
  - bestPractices
  - URL
author:
  - jacgit18
Purpose: This documentation discusses explains URI structure and best practices.
Status: Refinement
Started: 
EditDate: 2024-01-30
Relates: "[[Naming Conventions]]"
Peer Reviewed: 0
dg-publish: false
---
![[URL Structure.jpeg]]

A URI, or Universal Resource Identifier, is a concise character sequence identifying an abstract or physical resource. It serves as a versatile method for naming and locating web resources. Official examples highlight that any character sequence identifying a resource is considered a URI. The whole thing is considered the URI so `scheme/protocol` to the`Anchor/Fragment` which is optional this identifies something specific as a function of the [[Structuring URL#Document |document]]. ^9e3d3d

URL(Universal Resource Locator), a subset or URI that is used to find resources on the internet starts at  the`scheme/protocol` common ones are `HTTP` or `HTTPS`,  URL  ends at query `parameter` which consist of query string separator `?` and [[URI Query Design |Query String]] parameter. The URL also details access methods like HTTP or FTP.

A URN(Universal Resource Name), as another subset, functions as a distinctive name identifier, akin to a person's name. Notably, a URN holds persistent significance, ensuring that the owner can reliably anticipate that others or programs will consistently locate the associated resource. URN Start at the domain so after something  like`www` and goes all the way to the end at the Anchor/Fragment.

For example, a URN like `oasis:names:specification:docbook` differs from a resource name such as `linkedin.com/learning/instructors/morten-rand-hendrikson`. It's important to note that a URN can also function as a URL, but this is not mandatory. In the realm of REST APIs, the inclusive term URI is frequently employed, encompassing URLs, URNs, or a combination of both, offering flexibility in code implementations.

![[Url Process.gif]]

> A side note on hostnames: A hostname is a composition of the subdomain, domain, and top-level domain (TLD). For instance, examples like www.youtube.com or mail.gmail.com illustrate this combination. The top-level domain represents the most generic domain in the Internet's hierarchical DNS (Domain Name System), including familiar endings like `com`, `org`, and various others.
# URI Path Design Guidelines for REST APIs:
## 1. Naming Path Segments:
   - Each URI path segment, separated by forward slashes (/), presents a design opportunity.
   - Assigning meaningful values to path segments helps convey the hierarchical structure of the API's resource model.

## 2. Plural Nouns in Path Segments: 
   - Use plural nouns for collection and store names.
     - Example: `/leagues/seattle/teams/trebuchet/players`
   - Add '-s' for regular nouns to make them plural.
     - Example: `/categories/products`
   - Special cases include adding '-es' for nouns ending in -s, -ss, -sh, -ch, -x, or -z.
     - Example: `/addresses`

## 3. Resource Naming:
   - Singular nouns for document names.
     - Example: `/user/profile`
   - Plural nouns for collection and store names.
     - Example (Collection): `/leagues/seattle/teams/trebuchet/players`
     - Example (Store): `/user/favorites`
   - Use verbs or verb phrases for controller names.
     - Example: `/alerts/245743/resend`

## 4. Variable Path Segments:
   - Some path segments are static, others variable. URI templates allow clear naming of both.
     - Example: `/leagues/{leagueId}/teams/{teamId}/players/{playerId}`
     - Substitution: `/leagues/1/seattle/teams/5/trebuchet/players/21`

## 5. CRUD Functions:
   - Avoid using CRUD function names in URIs for clarity.
     - Preferred: `DELETE /users/1234`
     - Anti-patterns: `GET /deleteUser?id=1234`, `GET /deleteUser/1234`, `DELETE /deleteUser/1234`, `POST /users/1234/delete`

## 6. API URL Rules:
   - Use hyphens for readability.
   - Avoid underscores.
   - Prefer lowercase letters.
   - Exclude file extensions.
   - Maintain consistent subdomain names.
     - Example (Correct): `http://api.soccer.restapi.org`
     - Example (Incorrect): `http://api.soccer.rest_api.org`

## 7. Resource Modeling:
   - URI path reflects the API's resource model hierarchy.
     - Examples: `/leagues/seattle/teams/trebuchet`, `/leagues/seattle/teams`, `/leagues/seattle`, `/leagues`

## 8. **Resource Archetypes:**
### Document: 
  - Represents a singular concept, similar to an object instance or database record.
  - Its state representation typically includes fields with values and links to related resources.
  - The fundamental field and link-based structure make the document type the foundational archetype for other resource archetypes.

### Collection:
  - Acts as a server-managed directory of resources.
  - Clients may propose new resources for addition, but it's the collection's discretion to create or decline.
  - Decides the content and URIs of each contained resource.

### Store:
  - Functions as a client-managed resource repository.
  - Allows an API client to add, retrieve, and delete resources.
  - Stores do not create new resources independently; each stored resource has a URI chosen by the client upon initial insertion.

### Controller:
  - Differs from documents or collections, serving as executable functions.
  - Executed actions have parameters and return values, aligning with traditional web application HTML forms.
  - Responsible for application-specific actions, extending beyond standard HTTP methods (GET, POST, PUT, DELETE).
  - Typically, controller names appear as the last segment in a URI path, without child resources in the hierarchy.

### Examples illustrate their distinct characteristics:
- **Document:** `/leagues/seattle/teams/trebuchet/players/mike`
- **Collection:** `/leagues/seattle/teams/trebuchet/players`
- **Store:** `/user/favorites`
- **Controller:** `/alerts/245743/resend`

## 9. **Difference Between Route and Endpoint:**
   - Resource, Route, and Endpoint defined.
   - Routes locate resources, and endpoints are actions.
     - Resource: `{id: 42, type: employee, company: 5}`
     - Route: `localhost:8080/employees/42`
     - Endpoint: `GET localhost:8080/employees/42`

## 10. Smart Endpoints and Dumb Pipes:
   - Microservices principle suggests smart endpoints for logic and dumb pipes for simple data transfer/storage.
   - Enhances scalability and maintainability, though debugging may be challenging.
     - Example: Processing customer orders handled by a microservice rather than a centralized hub.

Here is a nice diagram which illustrate this principle:

![](https://miro.medium.com/v2/resize:fit:700/0*wB3H5DE2QXv8at0i.png)



