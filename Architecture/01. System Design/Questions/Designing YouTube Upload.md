---
excalidraw-plugin: parsed
tags: 
author: []
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-04-13T00:00:00.000Z
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---

# Question
## Requirements Gathering
Functional Requirements core functionality.

Non Requirements Functional how the system should perform or behave under various conditions things like performance, scalability, security, reliability, and usability should be discussed.


### Userbase

Geography USA no inappropriate content , China Region lock only certain content


#### Schema

##### Table 1

| Field     | Description                                | Type    |
| --------- | ------------------------------------------ | ------- |
| Latitude  | **\*** Lat of given location               | Double  |
| Longitude | **\*** Long of given location              | Double  |
| Radius    | **O** Default is 500 meters(about 3 miles) | Int     |
| tes       | ..                                         | VarChar |
| ..        | ..                                         | Char    |
| ..        | ..                                         | Boolean |


##### Table User

|     | User                | Type      |
| --- | ------------------- | --------- |
| PK  | UserID              | Integer   |
|     | email               | VarChar   |
|     | password            | VarChar   |
|     | date started        | TimeStamp |
|     | channel name        | VarChar   |
|     | monetization status | Boolean   |


##### Table Region

|     | Region   |
| --- | -------- |
| PK  | RegionID |
| FK  | UserID   |
| FK  | ...      |
|     | ...      |
|     | ...      |
|     | ...      |
|     | ...      |

  

### Capacity Estimation
Ask about or come up with DAU(Daily Active User) use a easy consistent value that's easy to calculate also consider ratios and metadata.

Assume we have a Active Userbase of 200,000,000

#### Storage
You should be concerned with writes here only because we need to know how much data we need to store.

##### Writes
> POST, PUT, DELETE

As a users we want to:
- Post Comment
- Post Like
- Not in scope for storage estimation
	- Post unlike(if you reClick like button) would still be a post
	- Update Comment 
	- Delete Comment

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

Total writes per day = 200,000,000 AU * 45,000 bytes Total Monthly Post size / 30 = 300,000,000,000 bytes = 286.1MB = 300MB


Total write per sec = 300,000,000,000 bytes/ 4000 * 20(secs in day est) = 300,000,000,000 bytes/ 80K = 300,000,000,000 bytes /100k = 3,000,000,000,000 bytes = 3TBps

###### Long term estimates

Data replication = 8TB Monthly Post Storage Requirement * 3 = 24TB

Year Storage =  1 * 400(Rounded year day) * 24TB = 400 * 24TB = 9600TB

5 Year Storage = Year Storage * 5 = 48,000TB = 48PB


#### Network Traffic
Read:Write *50*:1 read heavy ratio

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
caching is a way to serve read request faster use 80-20 rule for caching

Caching Memory = read per day * AVG post total size * 20%

Caching Memory = 172.5TB * 300 bytes  * 0.2 = 172.5TB * 300 bytes = 2,070TB  might be less since you have duplicate request being made to do the same thing 

Total memory: (Caching Memory * 3 for replication) = 6,210 TB


#### Bandwidth
InComing Data per sec(Write) = 0.005(write per sec) * 300 bytes(arbitrary storage action size) = 1.5 bytes per sec

OutGoing Data per sec(Read) = 0.25(read per sec) * 300 bytes(arbitrary storage action size) = 75 bytes per sec


Slow devices with low bandwidth maybe served lower resolution videos or content  
  
  
Versus fast devices with more bandwidth would be served high quality content like 4K, 1080p, etc

### App Server Estimations
Might be asked how many app service do you need

request per sec for single server = # cpu physical cores / 0.5 or half a sec = 16 

request per sec for single server = 8 physical cores / 0.5 or half a sec = 16 

Number of Servers = 500(read per sec)/ number of request per second a single server can handle

Number of Servers = 500(read per sec) / 16 request per sec for single server = 30 to 50 servers 



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
## Architecture
Typically Microservices 

Talk optimizations throughout and traffic management.

## Backing Services
Scalability strategies 
### Cloud Infrastructure
Don't need to use strictly cloud services

#### Data Storage
can talk governance and retention within cache, database, and application state also optimizations.
##### Database 

##### Storage 
file systems static files etc..

##### Caching

##### Networking

###### CDN
###### Traffic Management

###### Protocols

###### Security 

#### Processes

##### Compute

##### Data processing & analytics

##### Logging 

##### Monitoring

#### DevOPS
doesn't need to be cloud solution like AWS 


## Wrap Up


==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Excalidraw Data
## Text Elements
User Table ^zmns1Vak

## Element Links
cqasGqqJ: [[_System Design Template#Table 1]]
Mf9OBUwN: [[Designing YouTube Upload#Table User]]
gPBXehTo: [[Designing YouTube Upload#Table Region]]

%%
## Drawing
```compressed-json
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
```
%%