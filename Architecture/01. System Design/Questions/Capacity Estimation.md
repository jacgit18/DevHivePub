---
tags: 
author:
  - jacgit18
  - chatgpt
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-04-14
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Ask about or come up with DAU(Daily Active User) use a easy consistent value that's easy to calculate also consider ratios and metadata.

#todo/Med/Dev 
- [ ] Simplify and improve on math and approximation process and converting to different units.

Depending on interviewer you might be able to use a calculator.
#### Storage
You should be concerned with writes here only because we need to know how much data we need to store.

| Unit       | Equivalent in Bytes                           | Place                  |       |
| ---------- | --------------------------------------------- | ---------------------- | ----- |
| 1 Byte     | 1                                             | Hund over 2 digits     | 10^2  |
| 1 Kilobyte | 1,024 Bytes                                   | Thous over 3 digits    | 10^3  |
| 1 Megabyte | 1,024 Kilobytes = 1,048,576 Bytes             | Milli over 6 digits    | 10^6  |
| 1 Gigabyte | 1,024 Megabytes = 1,073,741,824 Bytes         | Billi over 9 digits    | 10^9  |
| 1 Terabyte | 1,024 Gigabytes = 1,099,511,627,776 Bytes     | Trilli over 12 digits  | 10^12 |
| 1 Petabyte | 1,024 Terabytes = 1,125,899,906,842,624 Bytes | Quadril over 15 digits | 10^15 |


| Calculation              | Result                                    |         |
| ------------------------ | ----------------------------------------- | ------- |
| 60 seconds * 60 minutes  | 3,600 seconds per hour use 4,000          | Monthly |
| 3,600 seconds * 24 hours | 86,400 seconds per day use 80,000         | Daily   |
| 86,400 seconds * 30 days | 2,592,000 seconds per month use 2,400,000 | Seconds |

After developing schema you can define general feature like below following a rough [[Structuring URL#URI Path Design Guidelines for REST APIs |endpoints naming convention]].

maybe consider defining some microservices here and weather they are following CQRS pattern meaning if you have services that exclusively handling reads and others handling just writes.
##### Writes
> POST, PUT, DELETE

###### Non Functional
**General Microservices**
Logging 
Security
Metrics
Monitoring

> **Simple math:** 14% of 50 just through reverse so 50% of 14 which is 7 

###### Functional
As a users we want to:
- Post Comment
- Post Like
- Not in scope for storage estimation
	- Post unlike(if you reClick like button) would still be a post
	- Update Comment 
	- Delete Comment

**General Microservices**: anything relating to the feature can be broken into several different microservices depends on the feature of focus.

*String Data*
Lets Assume were dealing with English comments there are about 500K words in the English language.

A comment might contain 20 to 40 words and each word might have a length of 5 characters thus each comment will range about 100 to 200 characters. Assuming each character is approximately 1 byte, the average size of a YouTube comment in English would be around 100 to 200 bytes.

**Lets say we have 2:1 ratio of Likes to Comments**
Active Userbase size = 200,000,000
AVG likes per user in month = 100 posts  
AVG comments per user in month = 50 posts 
Post per user in month = 150

###### Data Size 
AVG likes size = 90 byte(adjusted for meta data)

AVG comments size = 
40(words) * 5(char) * 1byte = 
200 byte(adjusted for meta data)

Total post size per user = round to 300 bytes 

Total Monthly Post size = 150 Post per user in month * 300 bytes Total post size per user = 45,000 bytes = 43.95KB = 44KB

Monthly Post Storage Requirement = AU size 200M * Total post size 300 bytes * 150 monthly post = 9,000,000,000,000 bytes = 8.18TB = 8TB

###### Daily estimates
#todo/Low/Dev  
- [ ] Double check calculations

Total writes per day = 200,000,000 AU * 45,000 bytes Total Monthly Post size / 30 = 300,000,000,000 bytes = 286.1MB = 300MB


Total write per sec = 300,000,000,000 bytes/ 4000 * 20(secs in day est) = 300,000,000,000 bytes/ 80K = 300,000,000,000 bytes /100k = 3,000,000,000,000 bytes = 3TBps

###### Long term estimates

> Data replication which is typically done 3 to 5 times  

Data replication = 8TB Monthly Post Storage Requirement * 3 = 24TB

Year Storage =  1 * 400(Rounded year day) * 24TB = 400 * 24TB = 9600TB

5 Year Storage = Year Storage * 5 = 48,000TB = 48PB

>When calculating storage for multiple years, it's essential to consider potential growth in data volume over time. A linear projection may not accurately reflect real-world growth patterns.


#### Network Traffic
Read:Write *50*:1 read heavy ratio

Reads will typically be higher since lot of systems are read heavy. 
##### Reads
> GET

As a users we want to:
- Get Video views(not included in calculation)
- Get Video likes
- Get Comment likes

something off with math

read per day = *50* * 300,000,000,000 bytes write per day = 15,000,000,000,000 bytes = 15,000TB = 15PB

read per sec = *50* * 3,000,000,000,000 bytes write per sec = 150,000,000,000,000 bytes = 150TB

Overall Traffic: (Daily active users * read per sec) * (Daily active users * writes per sec)

Overall Traffic = 200,000,000 AU * (15,000,000,000,000 bytes + 150,000,000,000,000 bytes)

Overall Traffic = 200,000,000 AU * 165,000,000,000,000 bytes = 33,000,000,000,000,000,000,000,000 bytes

#### Memory Cache
#todo/Low/Dev  
- [ ] Double check calculations

caching is a way to serve read request faster use 80-20 rule for caching

Caching Memory = read per day * AVG post total size * 20%

Caching Memory = 172.5TB * 300 bytes  * 0.2 = 172.5TB * 300 bytes = 2,070TB  might be less since you have duplicate request being made to do the same thing 

Total memory: (Caching Memory * 3 for replication) = 6,210 TB

#### [[Bandwidth Estimation |Bandwidth]] 
InComing Data per sec(Write) = 0.005(write per sec) * 300 bytes(arbitrary storage action size) = 1.5 bytes per sec

OutGoing Data per sec(Read) = 0.25(read per sec) * 300 bytes(arbitrary storage action size) = 75 bytes per sec

### App Server Estimations
Might be asked how many app service do you need

You should consider if the request is CPU bound, memory bound or I/O bound this relates to [[Request Resource Bound]]. 

If CPU bound the number of request per second for a single server would both depend on the server's hardware capabilities and the time it takes to process each single request.

request per sec for single server = # cpu physical cores / 0.5 or half a sec = 16 

request per sec for single server = 8 physical cores / 0.5 or half a sec = 16 

Number of Servers = 500(read per sec)/ number of request per second a single server can handle

Number of Servers = 500(read per sec) / 16 request per sec for single server = 30 to 50 servers 



