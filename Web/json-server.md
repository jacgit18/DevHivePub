---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Running `json-server` in your terminal is a straightforward process. `json-server` is a tool that allows you to create a fake REST API with zero coding. Here's how to set it up and run it:  
  
### Step 1: Install Node.js and npm  
If you haven't already installed Node.js and npm (Node Package Manager), you'll need to do that first. You can download and install them from the [Node.js website](https://nodejs.org/).  
  
### Step 2: Install `json-server`  
Once Node.js and npm are installed, you can install `json-server` globally using npm. Open your terminal and run the following command:  
  
```sh  
npm install -g json-server  
```  
  
The `-g` flag installs `json-server` globally on your system, making it available from any directory.  
  
### Step 3: Create a JSON file  
Create a `db.json` file in your project directory. This file will contain the data you want to serve via the REST API. For example:  
  
```json  
{  
"posts": [  
{ "id": 1, "title": "Hello World" }  
],  
"comments": [  
{ "id": 1, "body": "Nice post!", "postId": 1 }  
],  
"profile": { "name": "John Doe" }  
}  
```  
  
### Step 4: Run `json-server`  
Navigate to the directory where your `db.json` file is located and run the following command in your terminal:  
  
```sh  
json-server --watch db.json  
```  
  
This command starts `json-server` and watches for any changes in the `db.json` file. The server will be running at `http://localhost:3000` by default.  
  
### Step 5: Access the API  
You can now access the API endpoints in your browser or via tools like `curl` or Postman. For example:  
  
- List all posts: `http://localhost:3000/posts`  
- Get a specific post: `http://localhost:3000/posts/1`  
- List all comments: `http://localhost:3000/comments`  
- Get profile: `http://localhost:3000/profile`  
  
### Example of CRUD Operations  
You can perform CRUD (Create, Read, Update, Delete) operations on your JSON data using standard HTTP methods (`GET`, `POST`, `PUT`, `DELETE`).  
  
#### Create a new post  
```sh  
curl -X POST -H "Content-Type: application/json" -d '{"title": "New Post"}' http://localhost:3000/posts  
```  
  
#### Update a post  
```sh  
curl -X PUT -H "Content-Type: application/json" -d '{"title": "Updated Post"}' http://localhost:3000/posts/1  
```  
  
#### Delete a post  
```sh  
curl -X DELETE http://localhost:3000/posts/1  
```  
  
### Additional Options  
`json-server` has various options you can use:  
  
- Change the port: `json-server --watch db.json --port 4000`  
- Use a different file: `json-server --watch another-file.json`  
- Enable CORS: `json-server --watch db.json --cors`  
  
For more information and options, you can refer to the [json-server documentation](https://github.com/typicode/json-server).  
  
That's it! You now have a fully functional fake REST API running locally with `json-server`.