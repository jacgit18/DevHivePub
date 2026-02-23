---
excalidraw-plugin: parsed
tags: 
author: 
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: Refinement
Started: 2024-04-13T00:00:00.000Z
EditDate: 
Relates: 
Peer Reviewed: 0
excalidraw-open-md: true
dg-publish:
---
Design a simple library app for storing and organizing books. The app should allow users to:
## Userbase
All age groups in the use with potential global expansion

18 and above

adult level books


## Requirements Gathering
what part of the system frontend, backend, analytics, data pipeline, etc... 
#### Functional Requirements 
* Add books to their collection with details like title, author, and genre.
* Search for books in their collection by title or author.
* Organize books into categories like "Want to Read," "Currently Reading," and "Finished."
* Mark books as finished and rate them.

Nice to haves 

#### Non Requirements Functional
check age

service Oriented architecture 

distributed transaction potential pitfalls with multiple microservices connected to one db

talk tradeoffs of architecture
##### mainService
user Table 
##### collectionService
categories

##### bookService
bookStatus
bookRaitingating

##### bookSearch


### Schema

##### Table Definition 1

|     | User    |
| --- | ------- |
| PK  | userID  |
|     | addBook |
|     |         |
##### Table Definition 2
If you have multiple categories for a book, you can handle it by either:

  
1. Storing categories as a comma-separated list in a single column.  
2. Creating a separate table to store categories and then linking books to categories through a many-to-many relationship.

|     | Book          | Type    |
| --- | ------------- | ------- |
| PK  | bookID        |         |
|     | bookTitle     |         |
|     | bookGenre     |         |
|     | bookAuthor    |         |
|     | categories    | varChar |
|     | sub category  |         |
|     | OverallRating |         |

**Approach 1: Storing categories as a comma-separated list**  
  
In this approach, you would store categories as a comma-separated list in the `categories` column of the Book table.  
  
For example, if a book has categories "Fiction", "Thriller", and "Mystery", you would insert it like this:  
  
```sql  
-- Insert the book into the Book table
INSERT INTO Book (bookTitle, bookGenre, bookAuthor, categories, subCategory, OverallRating)  
VALUES ('The Da Vinci Code', 'Thriller', 'Dan Brown', 'Fiction, Thriller, Mystery', 'Suspense', 4.5);

-- Select books where 'Thriller' is one of the categories
SELECT * FROM Book WHERE FIND_IN_SET('Thriller', categories);
```

  
**Approach 2: Creating a separate table for categories**  
  
In this approach, you would create a separate table to store categories and then link books to categories through a many-to-many relationship using a junction table.  
  
First, create a Categories table:  
  
```sql  
CREATE TABLE Categories (  
categoryID INT PRIMARY KEY AUTO_INCREMENT,  
categoryName VARCHAR(255)  
);  
```  
  
Then, create a junction table to link books to categories:  
  
```sql  
CREATE TABLE BookCategories (  
bookID INT,  
categoryID INT,  
PRIMARY KEY (bookID, categoryID),  
FOREIGN KEY (bookID) REFERENCES Book(bookID),  
FOREIGN KEY (categoryID) REFERENCES Categories(categoryID)  
);  
```  
  
When inserting a book with multiple categories, you would first insert the categories into the Categories table if they don't already exist, and then insert the relationships into the BookCategories table.  
  
For example:  
  
1. Insert categories:  
```sql  
INSERT INTO Categories (categoryName) VALUES ('Fiction'), ('Thriller'), ('Mystery');  
```  
  
2. Insert book and link it to categories:  
```sql  
INSERT INTO Book (bookTitle, bookGenre, bookAuthor, subCategory, OverallRating)  
VALUES ('The Da Vinci Code', 'Thriller', 'Dan Brown', 'Suspense', 4.5);  
  
INSERT INTO BookCategories (bookID, categoryID) VALUES  
(LAST_INSERT_ID(), 1), -- Fiction  
(LAST_INSERT_ID(), 2), -- Thriller  
(LAST_INSERT_ID(), 3); -- Mystery  
```  
  
Approach 2 provides better normalization and allows for easier querying and management of categories. However, it requires more complex queries for insertion and retrieval.

###### Table Schema

| bookID | bookTitle | bookGenre | bookAuthor | categories | OverallRating |
| ------ | --------- | --------- | ---------- | ---------- | ------------- |
| 1      | tobe      | fafa      | tony       | horror     | 4             |
|        |           |           |            |            |               |
|        |           |           |            |            |               |
|        |           |           |            |            |               |
|        |           |           |            |            |               |
|        |           |           |            |            |               |
|        |           |           |            |            |               |




##### Table 3

|     | collection     |
| --- | -------------- |
| PK  | collectionID   |
| FK  | userID         |
| FK  | bookID         |
|     | bookCompletion |
|     | bookStatus     |
|     | rating         |





### Capacity Estimation
**AVG** - Average
**AFRS** - Average Feature Request Size by Bytes
**AFTRS** - Average Feature Total Req Size Per User
**AUS** - Active Userbase Size  
**DAU** - Daily Active Users 
**RPS** - Request Per Second

> **Lets say we have 2:1 ratio of feature A Request to feature B Request**
#### Storage
AUS = 
##### Writes
As a users we want a feature to:
- Post ... = 

##### Data Size 
AFRS One is about ...byte(adjusted for meta data)

AFRS Two is about ...byte(adjusted for meta data)

AFTRS = AFRS one ... + AFRS 

Monthly Estimation = 30 * AFTRS * AUS

###### Daily estimates
Write per day = AUS / Monthly Estimation

Write per sec = Write per day / 80,000

Write per user = AFTRS / AUS


###### Long term estimates

Data replication = Monthly Estimation * 3 or 5 = 

Year Storage = 1 * 400(Rounded year) * Replication

5 Year Storage = Year Storage * 5


#### Network Traffic
Read:Write *50*:1 read heavy ratio

##### Reads
As a users we want to:
- Get

Reads per day = *50* \* Write per day

Reads per sec = *50* \* Write per sec

Overall Traffic: (DAU * read per sec) * (DAU * writes per sec)

#### Memory Cache

Cache Memory = Read per day * AFTRS * 20% =

Total memory = Cache Memory * 3 or 5( replic) =

#### Bandwidth
> consider fast & slow lanes, also quality down-scaling and up-scaling

InComing Data per sec(Write) = (write per sec) * AFTRS = ... bytes per sec

OutGoing Data per sec(Read) = (read per sec) * AFTRS = ... bytes per sec


### App Server Estimations
CPU physical cores = ..

RPS for single server = # CPU physical cores / 0.5 or half a sec = ..

Number of Servers = ...(read per sec)/ ...RPS a single server can handle = ... servers






# Excalidraw Data
## Text Elements
 Main 
Service ^YPdxBgUk

Docker ^5vZ2NJCr

Frontend ^Ea4w1O0n

Web Application ^hO8OgX4X

G ^8mIRQbNi

o ^WBjTtbDU

o ^rbMpbviY

g ^OX2OdZ2b

l ^vyURZgnM

e ^oITVXDRZ

Mobile ^FVYiKQES

Lorem ipsum dolor sit amet, 
consectetur adipiscing elit,sed
 do eiusmod tempor incididunt
 ut labore et dolore magna
 aliqua. Ut enim ad miveniam,
 quis nostrud exercitaullamco 
laboris nisi ut aliquip ex ea 
ommodo consequat. Duis aute 
irure dolor in reprehenderit i ^78dPHWHy

Lorem ipsum dolor s, 
consectetur adipng d
 do eiusmopor incididunt
ut labore et dolore magna
aliqua. Ut enim ad miveniam,
quis nostrud exercitaullamco 
laboris nisi ut aliquip ex ea 
ommodo consequat. Duis aute 
 ^yP1Zg2zz

 Main 
Service ^mbskYkv5

API ^EhJ0BLrM

API ^qj7dnRO7

## Element Links
nHQ1vcRE: [[library app#Table 1]]
7s5CxVST: [[library app#Table 2]]

%%
## Drawing
```json
{
	"type": "excalidraw",
	"version": 2,
	"source": "https://github.com/zsviczian/obsidian-excalidraw-plugin/releases/tag/2.2.2",
	"elements": [
		{
			"type": "arrow",
			"version": 76,
			"versionNonce": 634704689,
			"index": "a1",
			"isDeleted": false,
			"id": "O5cZtrTZKiEwB_t1aFh44",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1025.526163634024,
			"y": -956.8393825840801,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 259.9999999999999,
			"height": 24,
			"seed": 991988465,
			"groupIds": [],
			"frameId": "b_CFDPxeHaDK177m8nPQ0",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716500790782,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": "arrow",
			"points": [
				[
					0,
					0
				],
				[
					259.9999999999999,
					24
				]
			]
		},
		{
			"type": "frame",
			"version": 167,
			"versionNonce": 1847116933,
			"index": "a2",
			"isDeleted": false,
			"id": "b_CFDPxeHaDK177m8nPQ0",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -1498.2029442210246,
			"y": -1137.7444537919764,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1191.3043086357386,
			"height": 792.0821704947901,
			"seed": 156896352,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716438729287,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "1 Schema"
		},
		{
			"type": "frame",
			"version": 1471,
			"versionNonce": 1184569311,
			"index": "bfL",
			"isDeleted": false,
			"id": "jVJ5sluGFDEwVB1RTu8aV",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -122.65702421065271,
			"y": -1110.7770995432054,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1280.2250212620368,
			"height": 730.4702604333786,
			"seed": 494278277,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "2. Architecture"
		},
		{
			"type": "frame",
			"version": 1397,
			"versionNonce": 2040289585,
			"index": "bgJ",
			"isDeleted": false,
			"id": "sYqN-8rYkxZWInFVviZMe",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -64.50765944312661,
			"y": 845.3814271285296,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1233.2330293478853,
			"height": 680.6011237473022,
			"seed": 891328773,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716482989564,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "6. Data Pipline"
		},
		{
			"type": "frame",
			"version": 1874,
			"versionNonce": 1091297695,
			"index": "blo",
			"isDeleted": false,
			"id": "e8NQeSlQO2kL4L22fKBfo",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -68.01527315339922,
			"y": -204.6930884727483,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1266.2337778857357,
			"height": 813.8321369772609,
			"seed": 387589093,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480959523,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "4. Security"
		},
		{
			"type": "ellipse",
			"version": 1470,
			"versionNonce": 279169509,
			"index": "bqF2",
			"isDeleted": false,
			"id": "t-bPmdwuOh5DzjsHc5Nby",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -890.82225817216,
			"y": -1662.9565251896101,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 110.70586688701928,
			"height": 107.83038982501878,
			"seed": 1928953477,
			"groupIds": [
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1415,
			"versionNonce": 2008761669,
			"index": "bqF4",
			"isDeleted": false,
			"id": "hZ5ih7UAKm4hctjEQAd0l",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -870.6939187381574,
			"y": -1651.454616941608,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 984704485,
			"groupIds": [
				"nO5JfQt9Np0ihHV4vvLc7",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1388,
			"versionNonce": 957109413,
			"index": "bqF8",
			"isDeleted": false,
			"id": "bVMDoxOLNFYkgEay4K6yc",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -863.505226083156,
			"y": -1644.2659242866066,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1169514821,
			"groupIds": [
				"nO5JfQt9Np0ihHV4vvLc7",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1390,
			"versionNonce": 4487173,
			"index": "bqFC",
			"isDeleted": false,
			"id": "MQaTX8N7I1R5hfVbzY_zJ",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -864.224095348656,
			"y": -1632.0451467731045,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 2036527269,
			"groupIds": [
				"nO5JfQt9Np0ihHV4vvLc7",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1400,
			"versionNonce": 660680549,
			"index": "bqFG",
			"isDeleted": false,
			"id": "V1TGWTyS7LASzm-buwZoE",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -864.224095348656,
			"y": -1617.6677614631026,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 862426117,
			"groupIds": [
				"nO5JfQt9Np0ihHV4vvLc7",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1468,
			"versionNonce": 1823472325,
			"index": "bqFI",
			"isDeleted": false,
			"id": "lkwweXjrmbFoaAkaqlCAM",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -857.0354026936545,
			"y": -1635.6394931006053,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 1069599589,
			"groupIds": [
				"U3GMaMSdcaZkbi6GLjNll",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1442,
			"versionNonce": 1758353957,
			"index": "bqFK",
			"isDeleted": false,
			"id": "V27UYF5EvN8mM3H99oJh6",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -849.8467100386531,
			"y": -1628.4508004456038,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 247207621,
			"groupIds": [
				"U3GMaMSdcaZkbi6GLjNll",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1444,
			"versionNonce": 1151978885,
			"index": "bqFO",
			"isDeleted": false,
			"id": "h1vr54NFZUDAGsjmacpOj",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -850.5655793041531,
			"y": -1616.2300229321017,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 720827941,
			"groupIds": [
				"U3GMaMSdcaZkbi6GLjNll",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1453,
			"versionNonce": 796906725,
			"index": "bqFS",
			"isDeleted": false,
			"id": "DK3de4-cxp1tDD-HS1myM",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -850.5655793041531,
			"y": -1601.8526376220998,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1868491141,
			"groupIds": [
				"U3GMaMSdcaZkbi6GLjNll",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1452,
			"versionNonce": 350089285,
			"index": "bqFV",
			"isDeleted": false,
			"id": "5y_FddFtMRsnm_exvDWbH",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -841.2202788526517,
			"y": -1625.575323383604,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 2100392165,
			"groupIds": [
				"cUPNNJAsdJIAnhp49x9oy",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1426,
			"versionNonce": 312582053,
			"index": "bqFX",
			"isDeleted": false,
			"id": "RD9GiDttDT6ZGbmd30zzP",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -834.0315861976503,
			"y": -1618.3866307286025,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1912343621,
			"groupIds": [
				"cUPNNJAsdJIAnhp49x9oy",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1428,
			"versionNonce": 788030213,
			"index": "bqFZ",
			"isDeleted": false,
			"id": "q41i6APUH8Z-MH184rLre",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -834.7504554631503,
			"y": -1606.1658532151005,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1570519973,
			"groupIds": [
				"cUPNNJAsdJIAnhp49x9oy",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1437,
			"versionNonce": 1314896485,
			"index": "bqFd",
			"isDeleted": false,
			"id": "4NJj5Y_k0XSVA-bq345hU",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -834.7504554631503,
			"y": -1591.7884679050976,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 2017427205,
			"groupIds": [
				"cUPNNJAsdJIAnhp49x9oy",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1469,
			"versionNonce": 1772430789,
			"index": "bqFh",
			"isDeleted": false,
			"id": "IIO-yd3tuoBXQevAgcrYx",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -829.7183706046505,
			"y": -1612.635676604601,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 409163365,
			"groupIds": [
				"4NJrRuYXmXqhB_Yptn_5c",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1443,
			"versionNonce": 65414437,
			"index": "bqFl",
			"isDeleted": false,
			"id": "he2PYvMqVGY1DN1OzFNVI",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -822.5296779496491,
			"y": -1605.4469839496005,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1758806469,
			"groupIds": [
				"4NJrRuYXmXqhB_Yptn_5c",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1445,
			"versionNonce": 1620064389,
			"index": "bqFp",
			"isDeleted": false,
			"id": "AtMBSTJobDGB0ncyzo6yO",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -823.2485472151491,
			"y": -1593.2262064360984,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1588773157,
			"groupIds": [
				"4NJrRuYXmXqhB_Yptn_5c",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1454,
			"versionNonce": 2036391909,
			"index": "bqFt",
			"isDeleted": false,
			"id": "tVggo1DQP82LEVa5fPW-n",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -823.2485472151491,
			"y": -1578.8488211260956,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1869173893,
			"groupIds": [
				"4NJrRuYXmXqhB_Yptn_5c",
				"kWu9_nzr_Steyw5MAjA_e",
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 1375,
			"versionNonce": 879074117,
			"index": "bqFx",
			"isDeleted": false,
			"id": "YPdxBgUk",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -879.3203499241588,
			"y": -1552.2506583025906,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 97.05978393554688,
			"height": 71.88692655001252,
			"seed": 112622565,
			"groupIds": [
				"lUqXv3CD9laM_U0IsOzLY",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false,
			"fontSize": 28.754770620005008,
			"fontFamily": 1,
			"text": " Main \nService",
			"rawText": " Main \nService",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": " Main \nService",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "rectangle",
			"version": 4244,
			"versionNonce": 1509681829,
			"index": "bqG",
			"isDeleted": false,
			"id": "c2tb1-mTCtEMW7MOzwIlZ",
			"fillStyle": "cross-hatch",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -817.4150705339778,
			"y": -1680.892773800303,
			"strokeColor": "#000000",
			"backgroundColor": "#ced4da",
			"width": 34.53052968780019,
			"height": 34.49746345013403,
			"seed": 1374289765,
			"groupIds": [
				"vpsz89i06Jw3fI26KORJX",
				"uQnAUzCj2x7Fm7NIgENhz",
				"s6DKVJUyjP6fmkCH8JXtn",
				"kNTM6JgNUgdYNKy1EbcVp",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "line",
			"version": 3478,
			"versionNonce": 1255230981,
			"index": "bqH",
			"isDeleted": false,
			"id": "LBT6pvEkLOEvlbzoqrBgB",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -809.3035601712306,
			"y": -1661.954382847628,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 30.330909389540505,
			"height": 14.881918378267327,
			"seed": 1839123141,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					14.195130198306623,
					-0.29759148014083747
				],
				[
					17.607239598653166,
					-0.7241033654635906
				],
				[
					16.899611749827677,
					-3.467357911231962
				],
				[
					18.024057706633045,
					-6.074904129852095
				],
				[
					19.759188206971423,
					-3.641841835857224
				],
				[
					19.526550241487776,
					-1.6837586868808927
				],
				[
					22.323121050747634,
					-3.5982213021310407
				],
				[
					24.50900211001461,
					-2.7985105409396454
				],
				[
					23.21007011345964,
					-1.0391441329272284
				],
				[
					20.35049007687475,
					0.31309957146695666
				],
				[
					12.886518579471334,
					7.995180896383552
				],
				[
					0.09112362214748661,
					8.807014248415232
				],
				[
					-5.821907279525893,
					0.5971166394518316
				],
				[
					-1.9193106428346574,
					-0.31988391399211813
				],
				[
					-0.15384376079201512,
					-0.010470031009590356
				]
			]
		},
		{
			"type": "rectangle",
			"version": 2383,
			"versionNonce": 1977828709,
			"index": "bqI",
			"isDeleted": false,
			"id": "TyXmSb0B-EMdrdznus_y6",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -812.6702848506227,
			"y": -1666.1392400112018,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 56830501,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2438,
			"versionNonce": 243224773,
			"index": "bqJ",
			"isDeleted": false,
			"id": "cuD_qvC8aijoc_iOThDzz",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -808.9430584662603,
			"y": -1666.275902775118,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 1411685765,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2458,
			"versionNonce": 37941285,
			"index": "bqK",
			"isDeleted": false,
			"id": "jeRv7Oy2Pz3n6MQegUQ5a",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -805.0418980342472,
			"y": -1666.2137888346906,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 656450789,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2479,
			"versionNonce": 790340485,
			"index": "bqL",
			"isDeleted": false,
			"id": "9TwaNHfNQEFCTDgMhxvbi",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -801.1531620585899,
			"y": -1666.4001431680172,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 2145697861,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2521,
			"versionNonce": 1497819877,
			"index": "bqM",
			"isDeleted": false,
			"id": "fgqwkNpUEm5D0TgewArLv",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -797.4632111286426,
			"y": -1666.3504495132684,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 340684709,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2425,
			"versionNonce": 1632781893,
			"index": "bqN",
			"isDeleted": false,
			"id": "2cKHgXa4jsEp70uyAOEm5",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -809.048667387973,
			"y": -1669.8913069669188,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 42676997,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2449,
			"versionNonce": 974861733,
			"index": "bqO",
			"isDeleted": false,
			"id": "Ea7xGML_o0WOOF3wdn7W0",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -805.1350804142619,
			"y": -1669.8416112268296,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 1192790629,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2473,
			"versionNonce": 516897029,
			"index": "bqP",
			"isDeleted": false,
			"id": "de3PqjoTKp69fxAmeTxfO",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -801.1717977004589,
			"y": -1669.8416153975068,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 1925445061,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2492,
			"versionNonce": 149672037,
			"index": "bqQ",
			"isDeleted": false,
			"id": "LHjkVDxfv1_9FRpb-bWmP",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -801.3022555348869,
			"y": -1673.643384349336,
			"strokeColor": "#0091e2",
			"backgroundColor": "#0091e2",
			"width": 2.981781941625904,
			"height": 2.981781941625904,
			"seed": 548074789,
			"groupIds": [
				"qQy_zM0YCMCtppoi8isGL",
				"nwfGX80AHOeWuLtb-iCCh",
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 3002,
			"versionNonce": 1715370949,
			"index": "bqR",
			"isDeleted": false,
			"id": "5vZ2NJCr",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -818.0950750825957,
			"y": -1643.5107621035859,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 35.32017517089844,
			"height": 13.39199208396871,
			"seed": 742066309,
			"groupIds": [
				"X9LmpFFtD9FFoLsxMBYDT",
				"0jtXrDQfxFQs9iPxULwgQ"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716439191891,
			"link": null,
			"locked": false,
			"fontSize": 10.713593667174967,
			"fontFamily": 1,
			"text": "Docker",
			"rawText": "Docker",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Docker",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "frame",
			"version": 1715,
			"versionNonce": 1797397361,
			"index": "br3",
			"isDeleted": false,
			"id": "Zw6i2EyRnYf5grMUEZe_L",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -35.22088268813104,
			"y": 1903.6355126859626,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1254.5671112190703,
			"height": 753.9344570806347,
			"seed": 1860750533,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716478739506,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "8. Devops"
		},
		{
			"type": "rectangle",
			"version": 803,
			"versionNonce": 206226431,
			"index": "br4",
			"isDeleted": false,
			"id": "30Z3aVjI_K1Z8-uKODJ_U",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -60.55081001851863,
			"y": -1001.7215216457582,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 166.82823768028857,
			"height": 159.60101536861666,
			"seed": 67914321,
			"groupIds": [
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 3
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 768,
			"versionNonce": 862972959,
			"index": "br5",
			"isDeleted": false,
			"id": "Ea4w1O0n",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1.086471737661867,
			"y": -998.7233821761972,
			"strokeColor": "#1e1e1e",
			"backgroundColor": "transparent",
			"width": 57.90040588378906,
			"height": 17.365890377836774,
			"seed": 26269745,
			"groupIds": [
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 13.89271230226942,
			"fontFamily": 1,
			"text": "Frontend",
			"rawText": "Frontend",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Frontend",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "text",
			"version": 1738,
			"versionNonce": 1744506943,
			"index": "br6",
			"isDeleted": false,
			"id": "hO8OgX4X",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 29.435897406835522,
			"y": -895.2902566049428,
			"strokeColor": "#000000",
			"backgroundColor": "#ced4da",
			"width": 70.05963134765625,
			"height": 12.793185067506482,
			"seed": 1594403345,
			"groupIds": [
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 9.476433383338145,
			"fontFamily": 1,
			"text": "Web Application",
			"rawText": "Web Application",
			"textAlign": "center",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Web Application",
			"autoResize": true,
			"lineHeight": 1.3499999999999985
		},
		{
			"type": "rectangle",
			"version": 3655,
			"versionNonce": 63746143,
			"index": "br7",
			"isDeleted": false,
			"id": "nk_0fWU0OtN7vk7noFctp",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 27.21615725686226,
			"y": -940.5580203958356,
			"strokeColor": "#000000",
			"backgroundColor": "#ffffff",
			"width": 74.55486995341946,
			"height": 44.62024912179215,
			"seed": 1164656625,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2897,
			"versionNonce": 1354058879,
			"index": "br8",
			"isDeleted": false,
			"id": "rlD2etTCtR_QRBgToOvst",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 27.319937773549597,
			"y": -940.545324030628,
			"strokeColor": "#000000",
			"backgroundColor": "#ced4da",
			"width": 74.0628231698222,
			"height": 7.268765138682771,
			"seed": 1388321233,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 3059,
			"versionNonce": 175465631,
			"index": "br9",
			"isDeleted": false,
			"id": "J1yQi0w4mDfICqUk_HgMd",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": 29.832632582447502,
			"y": -938.5724429847522,
			"strokeColor": "#000000",
			"backgroundColor": "#fa5252",
			"width": 2.9160836677481305,
			"height": 2.9160836677481305,
			"seed": 2015279025,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 3103,
			"versionNonce": 549288127,
			"index": "brA",
			"isDeleted": false,
			"id": "n8okbb5JxrUxcFS2cN8iO",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": 35.81567109560443,
			"y": -938.5724429847522,
			"strokeColor": "#000000",
			"backgroundColor": "#fab005",
			"width": 2.9160836677481305,
			"height": 2.9160836677481305,
			"seed": 397318545,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 3161,
			"versionNonce": 959318239,
			"index": "brB",
			"isDeleted": false,
			"id": "9n_Fs5EUf95D3aEkLWxgw",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": 42.06147508507382,
			"y": -938.3096775084307,
			"strokeColor": "#000000",
			"backgroundColor": "#40c057",
			"width": 2.9160836677481305,
			"height": 2.9160836677481305,
			"seed": 1655127921,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 1420,
			"versionNonce": 1901565183,
			"index": "brC",
			"isDeleted": false,
			"id": "8mIRQbNi",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 47.30741514043851,
			"y": -927.2062227242158,
			"strokeColor": "#228be6",
			"backgroundColor": "#ffffff",
			"width": 6.176483154296875,
			"height": 10.181033578562184,
			"seed": 2001742161,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.8315642912016825,
			"fontFamily": 1,
			"text": "G",
			"rawText": "G",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "G",
			"autoResize": true,
			"lineHeight": 1.2999999999999996
		},
		{
			"type": "text",
			"version": 1372,
			"versionNonce": 1622842655,
			"index": "brD",
			"isDeleted": false,
			"id": "WBjTtbDU",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 54.74740121708038,
			"y": -927.2062227242158,
			"strokeColor": "#d9480f",
			"backgroundColor": "#ffffff",
			"width": 4.3368377685546875,
			"height": 10.181033578562186,
			"seed": 1057019697,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.83156429120168,
			"fontFamily": 1,
			"text": "o",
			"rawText": "o",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "o",
			"autoResize": true,
			"lineHeight": 1.3000000000000003
		},
		{
			"type": "text",
			"version": 1379,
			"versionNonce": 1523032383,
			"index": "brE",
			"isDeleted": false,
			"id": "rbMpbviY",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 60.621074435481745,
			"y": -927.2062227242158,
			"strokeColor": "#fab005",
			"backgroundColor": "#ffffff",
			"width": 4.3368377685546875,
			"height": 10.181033578562186,
			"seed": 203475217,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.83156429120168,
			"fontFamily": 1,
			"text": "o",
			"rawText": "o",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "o",
			"autoResize": true,
			"lineHeight": 1.3000000000000003
		},
		{
			"type": "text",
			"version": 1386,
			"versionNonce": 1893671263,
			"index": "brF",
			"isDeleted": false,
			"id": "OX2OdZ2b",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 66.10316943932257,
			"y": -927.2062227242158,
			"strokeColor": "#228be6",
			"backgroundColor": "#ffffff",
			"width": 3.9219512939453125,
			"height": 10.181033578562182,
			"seed": 2015854321,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.831564291201678,
			"fontFamily": 1,
			"text": "g",
			"rawText": "g",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "g",
			"autoResize": true,
			"lineHeight": 1.3
		},
		{
			"type": "text",
			"version": 1388,
			"versionNonce": 877763967,
			"index": "brG",
			"isDeleted": false,
			"id": "vyURZgnM",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 70.80210801404345,
			"y": -927.2062227242158,
			"strokeColor": "#5c940d",
			"backgroundColor": "#ffffff",
			"width": 2.0588226318359375,
			"height": 10.181033578562182,
			"seed": 27031761,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.831564291201678,
			"fontFamily": 1,
			"text": "l",
			"rawText": "l",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "l",
			"autoResize": true,
			"lineHeight": 1.3
		},
		{
			"type": "text",
			"version": 1375,
			"versionNonce": 945788319,
			"index": "brH",
			"isDeleted": false,
			"id": "oITVXDRZ",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 73.93473373052385,
			"y": -927.2062227242158,
			"strokeColor": "#d9480f",
			"backgroundColor": "#ffffff",
			"width": 4.28204345703125,
			"height": 10.181033578562184,
			"seed": 1779906225,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 7.831564291201678,
			"fontFamily": 1,
			"text": "e",
			"rawText": "e",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "e",
			"autoResize": true,
			"lineHeight": 1.3000000000000003
		},
		{
			"type": "rectangle",
			"version": 1308,
			"versionNonce": 1413056959,
			"index": "brI",
			"isDeleted": false,
			"id": "uyXOaSVvWBP1pIzn4sSL2",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 39.8239203732909,
			"y": -914.9237193941813,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 47.94657693835673,
			"height": 7.065811338284149,
			"seed": 1413429393,
			"groupIds": [
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 1
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 1344,
			"versionNonce": 620755423,
			"index": "brJ",
			"isDeleted": false,
			"id": "JG-s9nfTWMQXGhdjMkdGa",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": 81.96643799805616,
			"y": -913.1572665596104,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 2.7999929312863627,
			"height": 2.407011467246172,
			"seed": 567017073,
			"groupIds": [
				"0p2uWQZ2b_DioztGyAHiP",
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "line",
			"version": 1342,
			"versionNonce": 1338205695,
			"index": "brK",
			"isDeleted": false,
			"id": "fqyjjeIMUzz-L3ggCUtFu",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 2,
			"opacity": 100,
			"angle": 0,
			"x": 84.70554092505043,
			"y": -910.7716697096918,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 1.424557807145693,
			"height": 1.8175392711858847,
			"seed": 293931089,
			"groupIds": [
				"0p2uWQZ2b_DioztGyAHiP",
				"SkYIFSkMHJa_dc-PwuoFv",
				"2ucdI1u3ruM6A0hH9obAH",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"startBinding": null,
			"endBinding": null,
			"lastCommittedPoint": null,
			"startArrowhead": null,
			"endArrowhead": null,
			"points": [
				[
					0,
					0
				],
				[
					1.424557807145693,
					1.8175392711858847
				]
			]
		},
		{
			"type": "text",
			"version": 1734,
			"versionNonce": 59002399,
			"index": "brL",
			"isDeleted": false,
			"id": "FVYiKQES",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -41.18864379528085,
			"y": -890.6403144519367,
			"strokeColor": "#000000",
			"backgroundColor": "#ced4da",
			"width": 30.623672485351562,
			"height": 13.703555621344236,
			"seed": 490853937,
			"groupIds": [
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 10.731992660175933,
			"fontFamily": 1,
			"text": "Mobile",
			"rawText": "Mobile",
			"textAlign": "center",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Mobile",
			"autoResize": true,
			"lineHeight": 1.276888277439391
		},
		{
			"type": "rectangle",
			"version": 2678,
			"versionNonce": 993210943,
			"index": "brM",
			"isDeleted": false,
			"id": "xbyz-T1rHlQH6LV_ShAZq",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -54.250133219173904,
			"y": -978.8494885550082,
			"strokeColor": "#000000",
			"backgroundColor": "#ced4da",
			"width": 56.78106383019672,
			"height": 86.83905308846738,
			"seed": 401205265,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 1
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2900,
			"versionNonce": 1068536415,
			"index": "brN",
			"isDeleted": false,
			"id": "mYjkJ4qv0qyUzgbtL-PLv",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -51.610421030780266,
			"y": -975.8036697474964,
			"strokeColor": "#000000",
			"backgroundColor": "#fff",
			"width": 50.91947293149188,
			"height": 81.0131115545097,
			"seed": 192200177,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 1
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 2915,
			"versionNonce": 1775038079,
			"index": "brO",
			"isDeleted": false,
			"id": "mWMsNkRbWBG8mEfGyuoAR",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -27.278785244721824,
			"y": -976.5528007755272,
			"strokeColor": "#000000",
			"backgroundColor": "#fff",
			"width": 3.5027361435934834,
			"height": 3.5027361435934834,
			"seed": 1458165713,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2569,
			"versionNonce": 608749215,
			"index": "brP",
			"isDeleted": false,
			"id": "wSPjidFcg7DZkD2EvSq8T",
			"fillStyle": "cross-hatch",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -49.218918690419315,
			"y": -969.9522113637527,
			"strokeColor": "#000000",
			"backgroundColor": "#15aabf",
			"width": 45.75035870892651,
			"height": 21.35302679524112,
			"seed": 207664561,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2598,
			"versionNonce": 768907967,
			"index": "brQ",
			"isDeleted": false,
			"id": "s9BvDLkx9aWg3YC64rn5z",
			"fillStyle": "cross-hatch",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -46.1300423558213,
			"y": -944.1445448197129,
			"strokeColor": "#000000",
			"backgroundColor": "#fab005",
			"width": 16.019923988425816,
			"height": 12.47250733327335,
			"seed": 251713425,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2647,
			"versionNonce": 454093535,
			"index": "brR",
			"isDeleted": false,
			"id": "B-vMcV67zLRbr0qnIUPKg",
			"fillStyle": "cross-hatch",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -20.50418455883993,
			"y": -920.2444545168836,
			"strokeColor": "#000000",
			"backgroundColor": "#fab005",
			"width": 14.475485821127082,
			"height": 10.541959624149936,
			"seed": 1895939441,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": null,
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 1595,
			"versionNonce": 411973375,
			"index": "brS",
			"isDeleted": false,
			"id": "78dPHWHy",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -27.16638515396449,
			"y": -945.2721202758669,
			"strokeColor": "#495057",
			"backgroundColor": "transparent",
			"width": 25.628448486328125,
			"height": 20.84991525853299,
			"seed": 296413009,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 1.690218756656126,
			"fontFamily": 1,
			"text": "Lorem ipsum dolor sit amet, \nconsectetur adipiscing elit,sed\n do eiusmod tempor incididunt\n ut labore et dolore magna\n aliqua. Ut enim ad miveniam,\n quis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \nirure dolor in reprehenderit i",
			"rawText": "Lorem ipsum dolor sit amet, \nconsectetur adipiscing elit,sed\n do eiusmod tempor incididunt\n ut labore et dolore magna\n aliqua. Ut enim ad miveniam,\n quis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \nirure dolor in reprehenderit i",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Lorem ipsum dolor sit amet, \nconsectetur adipiscing elit,sed\n do eiusmod tempor incididunt\n ut labore et dolore magna\n aliqua. Ut enim ad miveniam,\n quis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \nirure dolor in reprehenderit i",
			"autoResize": true,
			"lineHeight": 1.3706256908018875
		},
		{
			"type": "text",
			"version": 1638,
			"versionNonce": 1825373983,
			"index": "brT",
			"isDeleted": false,
			"id": "yP1Zg2zz",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 80,
			"angle": 0,
			"x": -48.209355183410246,
			"y": -928.2942538977602,
			"strokeColor": "#495057",
			"backgroundColor": "transparent",
			"width": 25.628448486328125,
			"height": 20.84991525853299,
			"seed": 2069091633,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 2
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false,
			"fontSize": 1.690218756656126,
			"fontFamily": 1,
			"text": "Lorem ipsum dolor s, \nconsectetur adipng d\n do eiusmopor incididunt\nut labore et dolore magna\naliqua. Ut enim ad miveniam,\nquis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \n",
			"rawText": "Lorem ipsum dolor s, \nconsectetur adipng d\n do eiusmopor incididunt\nut labore et dolore magna\naliqua. Ut enim ad miveniam,\nquis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \n",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "Lorem ipsum dolor s, \nconsectetur adipng d\n do eiusmopor incididunt\nut labore et dolore magna\naliqua. Ut enim ad miveniam,\nquis nostrud exercitaullamco \nlaboris nisi ut aliquip ex ea \nommodo consequat. Duis aute \n",
			"autoResize": true,
			"lineHeight": 1.3706256908018875
		},
		{
			"type": "rectangle",
			"version": 2700,
			"versionNonce": 977126207,
			"index": "brU",
			"isDeleted": false,
			"id": "Y_ibbKB-xWE7nG4G5X__S",
			"fillStyle": "cross-hatch",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -48.7812224694379,
			"y": -906.7282392217635,
			"strokeColor": "#000000",
			"backgroundColor": "#15aabf",
			"width": 45.75035870892651,
			"height": 7.351567790824185,
			"seed": 23332625,
			"groupIds": [
				"bqvIp1Q7dwlL1nNlJ2I8W",
				"tAzMVsQzlmhdWK9HJDnq1",
				"jMAwa3PZwIrjE0KZwFMPM"
			],
			"frameId": "jVJ5sluGFDEwVB1RTu8aV",
			"roundness": {
				"type": 1
			},
			"boundElements": [],
			"updated": 1716480948061,
			"link": null,
			"locked": false
		},
		{
			"type": "frame",
			"version": 1151,
			"versionNonce": 172114623,
			"index": "buz",
			"isDeleted": false,
			"id": "0TiHyi087yAXlumZJ9odr",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -1470.0281698155422,
			"y": -166.5653335572988,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1136.188263721955,
			"height": 681.5320763221152,
			"seed": 1766082463,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716478759471,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "3. Database"
		},
		{
			"type": "frame",
			"version": 1390,
			"versionNonce": 1768928671,
			"index": "c08e",
			"isDeleted": false,
			"id": "rSPLAZf91HoAXp5U5_E4A",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -1439.6474897060184,
			"y": 784.4814139887567,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1108.6882637219555,
			"height": 781.5320763221152,
			"seed": 1585011377,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716478820915,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "5. Networking Performance"
		},
		{
			"type": "frame",
			"version": 1527,
			"versionNonce": 1100855487,
			"index": "c0DS",
			"isDeleted": false,
			"id": "SwW90nKVcIpgngPdfm7Ft",
			"fillStyle": "solid",
			"strokeWidth": 2,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -1441.3141563726845,
			"y": 1903.8147473220902,
			"strokeColor": "#bbb",
			"backgroundColor": "transparent",
			"width": 1207.0215970552886,
			"height": 741.5320763221146,
			"seed": 1837088113,
			"groupIds": [],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716478883566,
			"link": null,
			"locked": false,
			"customData": {
				"frameColor": {
					"stroke": "#D4D4D4",
					"fill": "#ADADAD",
					"nameColor": "#7A7A7A"
				}
			},
			"name": "7. Processes"
		},
		{
			"type": "ellipse",
			"version": 939,
			"versionNonce": 739064863,
			"index": "c0DU",
			"isDeleted": false,
			"id": "3GggliKN4lefWLfaMLRlV",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -624.1562912885524,
			"y": -1637.6299851580966,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 110.70586688701928,
			"height": 107.83038982501878,
			"seed": 508848703,
			"groupIds": [
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 883,
			"versionNonce": 7233599,
			"index": "c0DV",
			"isDeleted": false,
			"id": "ch9PdhcuIM1KA6NTtQFUg",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -604.027951854549,
			"y": -1626.1280769100945,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 434817631,
			"groupIds": [
				"A6IWOKCWp3qpG0OId2DJj",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 856,
			"versionNonce": 1364590687,
			"index": "c0DW",
			"isDeleted": false,
			"id": "e-S0kh_4NdULXEOvkxFNV",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -596.8392591995478,
			"y": -1618.9393842550935,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1879058047,
			"groupIds": [
				"A6IWOKCWp3qpG0OId2DJj",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 858,
			"versionNonce": 1083481215,
			"index": "c0DX",
			"isDeleted": false,
			"id": "qhsIo4gjnRA4odS1wqSah",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -597.5581284650477,
			"y": -1606.718606741591,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1867841183,
			"groupIds": [
				"A6IWOKCWp3qpG0OId2DJj",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 867,
			"versionNonce": 1642771615,
			"index": "c0DY",
			"isDeleted": false,
			"id": "Do-9jBB6FFS4fEHn8K_Sw",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -597.5581284650477,
			"y": -1592.3412214315886,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 983159487,
			"groupIds": [
				"A6IWOKCWp3qpG0OId2DJj",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 936,
			"versionNonce": 2097727679,
			"index": "c0DZ",
			"isDeleted": false,
			"id": "bfhZ6p04i0qrVk_BoZb9a",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -590.3694358100465,
			"y": -1610.3129530690917,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 1248797407,
			"groupIds": [
				"s9AZo8cxw8XIqyqpJ7_Vp",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 910,
			"versionNonce": 261052639,
			"index": "c0Da",
			"isDeleted": false,
			"id": "MmVBplPJRdSYUHT_s4F_f",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -583.1807431550453,
			"y": -1603.1242604140907,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 795176703,
			"groupIds": [
				"s9AZo8cxw8XIqyqpJ7_Vp",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 912,
			"versionNonce": 252634367,
			"index": "c0Db",
			"isDeleted": false,
			"id": "eUg4IHfYu3INBoQ92tKkp",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -583.8996124205455,
			"y": -1590.9034829005882,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 335361823,
			"groupIds": [
				"s9AZo8cxw8XIqyqpJ7_Vp",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 921,
			"versionNonce": 1795681567,
			"index": "c0Dc",
			"isDeleted": false,
			"id": "rWt0mDCZbZtZlJt5ui8U3",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -583.8996124205455,
			"y": -1576.5260975905862,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 2124872511,
			"groupIds": [
				"s9AZo8cxw8XIqyqpJ7_Vp",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 920,
			"versionNonce": 1324020031,
			"index": "c0Dd",
			"isDeleted": false,
			"id": "wP58hDIi0p-DgdniRAvIy",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -574.5543119690437,
			"y": -1600.24878335209,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 1405303647,
			"groupIds": [
				"hsrqgYEVrNmabAHTJ_L0p",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 894,
			"versionNonce": 605581663,
			"index": "c0De",
			"isDeleted": false,
			"id": "MKSSAF90CAtw6MrN1OyN8",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -567.3656193140425,
			"y": -1593.060090697089,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 396523391,
			"groupIds": [
				"hsrqgYEVrNmabAHTJ_L0p",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 896,
			"versionNonce": 1407249791,
			"index": "c0Df",
			"isDeleted": false,
			"id": "44kp3cZraK4N7ttPoIsyG",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -568.0844885795427,
			"y": -1580.839313183587,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1887776671,
			"groupIds": [
				"hsrqgYEVrNmabAHTJ_L0p",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 905,
			"versionNonce": 1233446303,
			"index": "c0Dg",
			"isDeleted": false,
			"id": "O98cLd3KsG_h0CYSvy88A",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -568.0844885795427,
			"y": -1566.461927873584,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1755046847,
			"groupIds": [
				"hsrqgYEVrNmabAHTJ_L0p",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 937,
			"versionNonce": 875878847,
			"index": "c0Dh",
			"isDeleted": false,
			"id": "YCUgg0XdMsopyJyQDT9_X",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -563.0524037210419,
			"y": -1587.309136573088,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 24.441555027004263,
			"height": 48.88311005400853,
			"seed": 1879512031,
			"groupIds": [
				"hDUmrGWrJJB3awWsnCg3c",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 911,
			"versionNonce": 152127967,
			"index": "c0Di",
			"isDeleted": false,
			"id": "_BqhZ-w3Ncvn_S4AzgETm",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -555.8637110660407,
			"y": -1580.1204439180865,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 517423103,
			"groupIds": [
				"hDUmrGWrJJB3awWsnCg3c",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 913,
			"versionNonce": 1160427007,
			"index": "c0Dj",
			"isDeleted": false,
			"id": "e0Gw0KXwQKSBv9cCH2AOG",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -556.5825803315406,
			"y": -1567.8996664045844,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 923592735,
			"groupIds": [
				"hDUmrGWrJJB3awWsnCg3c",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 922,
			"versionNonce": 1870765599,
			"index": "c0Dk",
			"isDeleted": false,
			"id": "xY4Sn8VrLHywSZvE5ts4T",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -556.5825803315406,
			"y": -1553.522281094582,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 12.939646779002253,
			"height": 4.313215593000751,
			"seed": 1721273407,
			"groupIds": [
				"hDUmrGWrJJB3awWsnCg3c",
				"j88M5Q3n7Kef6PWpp4DfT",
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 844,
			"versionNonce": 1527153215,
			"index": "c0Dl",
			"isDeleted": false,
			"id": "mbskYkv5",
			"fillStyle": "solid",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -612.6543830405503,
			"y": -1526.924118271077,
			"strokeColor": "#000000",
			"backgroundColor": "#ffcf66",
			"width": 97.05978393554688,
			"height": 71.88692655001252,
			"seed": 1230679135,
			"groupIds": [
				"2CyE7VsdKvUbXGpJ1nvQq"
			],
			"frameId": null,
			"roundness": null,
			"boundElements": [],
			"updated": 1716480076762,
			"link": null,
			"locked": false,
			"fontSize": 28.754770620005008,
			"fontFamily": 1,
			"text": " Main \nService",
			"rawText": " Main \nService",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": " Main \nService",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "text",
			"version": 1070,
			"versionNonce": 1100118879,
			"index": "c0Dn",
			"isDeleted": false,
			"id": "EhJ0BLrM",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -576.7677011544347,
			"y": 948.6767496577244,
			"strokeColor": "#343a40",
			"backgroundColor": "#e6f6fd",
			"width": 26.15533447265625,
			"height": 17.579354229737397,
			"seed": 1827498225,
			"groupIds": [
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false,
			"fontSize": 14.063483383789917,
			"fontFamily": 1,
			"text": "API",
			"rawText": "API",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "API",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "rectangle",
			"version": 2811,
			"versionNonce": 160020351,
			"index": "c0Do",
			"isDeleted": false,
			"id": "dZ0kgE_UeX2oCc6DCDrtm",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -593.1171740766874,
			"y": 857.2830684397256,
			"strokeColor": "#343a40",
			"backgroundColor": "#c5bcdd",
			"width": 61.77965267575575,
			"height": 84.19325967758246,
			"seed": 2048205521,
			"groupIds": [
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2286,
			"versionNonce": 595881887,
			"index": "c0Dp",
			"isDeleted": false,
			"id": "RVlCnw-1n5OMqJBF54GXu",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -565.4547846305823,
			"y": 867.4668046701792,
			"strokeColor": "#343a40",
			"backgroundColor": "#fff",
			"width": 41.02032438545285,
			"height": 21.095225075684876,
			"seed": 1642766513,
			"groupIds": [
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "text",
			"version": 1400,
			"versionNonce": 2041783231,
			"index": "c0Dq",
			"isDeleted": false,
			"id": "qj7dnRO7",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -558.9219384579942,
			"y": 870.5762070330584,
			"strokeColor": "#343a40",
			"backgroundColor": "#c5bcdd",
			"width": 26.15533447265625,
			"height": 17.579354229737397,
			"seed": 303391377,
			"groupIds": [
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false,
			"fontSize": 14.063483383789917,
			"fontFamily": 1,
			"text": "API",
			"rawText": "API",
			"textAlign": "left",
			"verticalAlign": "top",
			"containerId": null,
			"originalText": "API",
			"autoResize": true,
			"lineHeight": 1.25
		},
		{
			"type": "ellipse",
			"version": 1698,
			"versionNonce": 1547064287,
			"index": "c0Dr",
			"isDeleted": false,
			"id": "R8xFu83diqZLMgQSWXzLO",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -573.2196230868326,
			"y": 905.759270019499,
			"strokeColor": "#343a40",
			"backgroundColor": "#e6f6fd",
			"width": 21.305787760189357,
			"height": 21.305787760189357,
			"seed": 1464658033,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "ellipse",
			"version": 2016,
			"versionNonce": 1126072319,
			"index": "c0Ds",
			"isDeleted": false,
			"id": "eddIRW0AGZvnu1pY5mzV3",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -568.056077122911,
			"y": 910.7220817332683,
			"strokeColor": "#343a40",
			"backgroundColor": "#e6f6fd",
			"width": 10.86325670528099,
			"height": 11.363167079517385,
			"seed": 2069410385,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1748,
			"versionNonce": 1349265439,
			"index": "c0Dt",
			"isDeleted": false,
			"id": "AYsp6PxF96ce2ByZlWhRg",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0,
			"x": -564.4777876140589,
			"y": 901.2215358416222,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.408503961025831,
			"seed": 588267569,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1831,
			"versionNonce": 303025215,
			"index": "c0Du",
			"isDeleted": false,
			"id": "DESEGx5Crr5PzThUpUGbM",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 0.8972347895151316,
			"x": -555.1519925515427,
			"y": 905.2005102162652,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.446941791662069,
			"seed": 1817907729,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2065,
			"versionNonce": 65662047,
			"index": "c0Dv",
			"isDeleted": false,
			"id": "O8KTFZyOtktct6tR59IfL",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 3.1207322519217655,
			"x": -564.1558219265428,
			"y": 927.2732004892297,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.143121517942192,
			"seed": 1278257137,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 1971,
			"versionNonce": 1372260479,
			"index": "c0Dw",
			"isDeleted": false,
			"id": "aWJZOyMVthuxNp0XxEE-E",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 1.5305380278197802,
			"x": -551.656298140054,
			"y": 913.9914789892499,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.248790480137253,
			"seed": 748192209,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2022,
			"versionNonce": 1500749983,
			"index": "c0Dx",
			"isDeleted": false,
			"id": "Weyn0RqIZho8NhTXlXoKr",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 4.693036770078681,
			"x": -577.4174043756689,
			"y": 914.4657539055744,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.341618831872379,
			"seed": 1252663217,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2129,
			"versionNonce": 1821652159,
			"index": "c0Dy",
			"isDeleted": false,
			"id": "G4oB2m1xU5ZBvcdqZdscm",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 2.1603523389397683,
			"x": -554.6772501882145,
			"y": 922.5032631643205,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.2193423166412725,
			"seed": 1418527121,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2334,
			"versionNonce": 1389184223,
			"index": "c0Dz",
			"isDeleted": false,
			"id": "uyqCjyOjiPZPhdQCIHMJ3",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 3.8094800774607407,
			"x": -573.1891299581848,
			"y": 923.9326907931736,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.405380457958838,
			"seed": 1199089521,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "rectangle",
			"version": 2545,
			"versionNonce": 196038911,
			"index": "c0E0",
			"isDeleted": false,
			"id": "ID--M_Lz6nSpgs5k0H70D",
			"fillStyle": "solid",
			"strokeWidth": 4,
			"strokeStyle": "solid",
			"roughness": 0,
			"opacity": 100,
			"angle": 5.530741298209705,
			"x": -573.8239374777205,
			"y": 905.1026188849879,
			"strokeColor": "#343a40",
			"backgroundColor": "#000",
			"width": 4.034161109099681,
			"height": 4.191680572676076,
			"seed": 229937489,
			"groupIds": [
				"4VW97iEb5kBhCg6n-bqtg",
				"xKVp5YU06lxUPOH6Z1-O1",
				"m6dDuECfZoyV13cmH4SS0"
			],
			"frameId": "rSPLAZf91HoAXp5U5_E4A",
			"roundness": null,
			"boundElements": [],
			"updated": 1716482468025,
			"link": null,
			"locked": false
		},
		{
			"type": "embeddable",
			"version": 116,
			"versionNonce": 1047351986,
			"index": "c0E1",
			"isDeleted": false,
			"id": "nHQ1vcRE",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -1315.852961019645,
			"y": -1027.2446113422498,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 365.33333333333337,
			"height": 225.33333333333348,
			"seed": 91427,
			"groupIds": [],
			"frameId": "b_CFDPxeHaDK177m8nPQ0",
			"roundness": null,
			"boundElements": [],
			"updated": 1716499307968,
			"link": "[[library app#Table 1]]",
			"locked": false,
			"customData": {
				"mdProps": {
					"useObsidianDefaults": false,
					"backgroundMatchCanvas": false,
					"backgroundMatchElement": true,
					"backgroundColor": "#fff",
					"backgroundOpacity": 60,
					"borderMatchElement": true,
					"borderColor": "#fff",
					"borderOpacity": 0,
					"filenameVisible": false
				}
			},
			"scale": [
				1,
				1
			]
		},
		{
			"type": "embeddable",
			"version": 123,
			"versionNonce": 1150083890,
			"index": "c0E2",
			"isDeleted": false,
			"id": "7s5CxVST",
			"fillStyle": "hachure",
			"strokeWidth": 1,
			"strokeStyle": "solid",
			"roughness": 1,
			"opacity": 100,
			"angle": 0,
			"x": -816.1928303006907,
			"y": -1008.1727159174136,
			"strokeColor": "#000000",
			"backgroundColor": "transparent",
			"width": 360,
			"height": 412,
			"seed": 23157,
			"groupIds": [],
			"frameId": "b_CFDPxeHaDK177m8nPQ0",
			"roundness": null,
			"boundElements": [],
			"updated": 1716499323085,
			"link": "[[library app#Table 2]]",
			"locked": false,
			"customData": {
				"mdProps": {
					"useObsidianDefaults": false,
					"backgroundMatchCanvas": false,
					"backgroundMatchElement": true,
					"backgroundColor": "#fff",
					"backgroundOpacity": 60,
					"borderMatchElement": true,
					"borderColor": "#fff",
					"borderOpacity": 0,
					"filenameVisible": false
				}
			},
			"scale": [
				1,
				1
			]
		}
	],
	"appState": {
		"theme": "light",
		"viewBackgroundColor": "#ffffff",
		"currentItemStrokeColor": "#1e1e1e",
		"currentItemBackgroundColor": "transparent",
		"currentItemFillStyle": "solid",
		"currentItemStrokeWidth": 2,
		"currentItemStrokeStyle": "solid",
		"currentItemRoughness": 1,
		"currentItemOpacity": 100,
		"currentItemFontFamily": 1,
		"currentItemFontSize": 20,
		"currentItemTextAlign": "left",
		"currentItemStartArrowhead": null,
		"currentItemEndArrowhead": "arrow",
		"scrollX": 1664.8594969673572,
		"scrollY": 1277.2352159174134,
		"zoom": {
			"value": 0.7500000000000001
		},
		"currentItemRoundness": "round",
		"gridSize": null,
		"gridColor": {
			"Bold": "#C9C9C9FF",
			"Regular": "#EDEDEDFF"
		},
		"currentStrokeOptions": null,
		"previousGridSize": null,
		"frameRendering": {
			"enabled": true,
			"clip": true,
			"name": true,
			"outline": true
		},
		"objectsSnapModeEnabled": false
	},
	"files": {}
}
```
%%