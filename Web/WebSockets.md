---
tags:
  - web
  - protocol
  - scalability
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses web sockets and when to use them.
Status: Done
Started: 
EditDate: 2024-01-29
Relates: 
Peer Reviewed: 0
dg-publish: true
---
WebSocket is a communication protocol facilitating two-way streaming over a single TCP connection, commonly between web clients and servers but also employed for server-to-server interactions. Major browsers support WebSocket, making it prevalent in real-time applications.

Examples include Slack utilizing WebSockets to relay diverse workspace events, and Trello employing them to transmit server changes to listening browsers. Blockchain leverages its WebSocket API for real-time notifications on transactions and blocks.

WebSockets offer low-overhead full-duplex communication, crucial for real-time interactions, and can function over ports 80 or 443, bypassing firewall restrictions. Enterprise developers, concerned with security, may prefer WebSocket APIs over WebHooks, avoiding the need to expose an HTTP endpoint.

While advantageous for live streaming and prolonged connections, caution is warranted for mobile or unreliable connectivity scenarios. Clients must maintain connections, and scalability issues arise; developers managing multiple connections, as seen with Slack's WebSocket API, face challenges, especially in maintaining numerous connections for widespread app installations.

## WebSockets use cases
WebSockets are versatile and can be used in various contexts where real-time, bidirectional communication is beneficial. 
### Additional Contexts for WebSocket Usage:  
  
1. **Collaborative Editing:**  
- WebSockets can be used to enable real-time collaborative editing in applications where multiple users are working on the same document simultaneously. Changes made by one user can be instantly reflected for others.  
  
2. **Financial Applications:**  
- Trading platforms and financial applications often use WebSockets to provide real-time updates on stock prices, market changes, and trade executions.  
  
3. **Notifications and Alerts:**  
- WebSockets are suitable for building notification systems where users receive instant alerts about events or updates relevant to them, such as new messages, social media interactions, or system notifications.  
  
4. **Live Sports Updates:**  
- Sports applications can utilize WebSockets to deliver live scores, game updates, and commentary in real time to users.  
  
5. **IoT (Internet of Things):**  
- WebSockets are employed in IoT scenarios where devices need to communicate with a central server or with each other in real time.  
  
### Decision Considerations for WebSocket Usage:  
  
1. **Real-Time Requirements:**  
- Consider using WebSockets when real-time communication is essential for your application. If timely updates and low-latency interactions are crucial, WebSockets offer a more responsive solution compared to traditional HTTP.  
  
2. **Reduced Latency:**  
- If your application requires reduced latency for data transmission, WebSockets can provide a more efficient and immediate communication channel compared to polling or long-polling mechanisms.  
  
3. **Bidirectional Communication:**  
- When your application involves bidirectional communication, where both the server and the client need to send messages independently, WebSockets are a suitable choice.  
  
4. **Scalability:**  
- WebSockets can be more scalable in certain scenarios where maintaining a persistent connection for real-time updates is more efficient than repeatedly opening and closing connections.  
  
5. **Implementation Complexity:**  
- Assess the complexity of your use case. While WebSockets offer benefits for real-time applications, they also introduce additional complexities in terms of server-side handling and potential challenges related to load balancing.  
  
### Example:  
  
**Chat Application:**  
- Consider a chat application where users exchange messages in real time. WebSockets would be a suitable choice to deliver messages instantly to all connected users without the need for constant polling or delays associated with traditional HTTP.  
  
In conclusion, WebSockets are a powerful tool for scenarios requiring real-time, bidirectional communication. Evaluate the specific needs of your application, and if responsiveness, low latency, and bidirectional communication are critical, WebSockets may be a beneficial choice.



## WebSocket Example

1. **Server-side (Node.js):**

   The server-side code remains the same:

   ```javascript
   const WebSocket = require('ws');
   const server = new WebSocket.Server({ port: 3000 });

   server.on('connection', (socket) => {
       console.log('Client connected');

       // Handle messages from clients
       socket.on('message', (message) => {
           console.log(`Received: ${message}`);
           
           // Send a response back to the client
           socket.send('Server received your message');
       });

       // Handle disconnect
       socket.on('close', () => {
           console.log('Client disconnected');
       });
   });
   ```

2. **Client-side (React):**

   Create a React component that handles the WebSocket connection and communication:

   ```jsx
   import React, { useEffect } from 'react';

   const WebSocketExample = () => {
       useEffect(() => {
           const socket = new WebSocket('ws://localhost:3000');

           // Connection opened
           socket.addEventListener('open', (event) => {
               console.log('Connected to server');
               socket.send('Hello, server!');
           });

           // Listen for messages
           socket.addEventListener('message', (event) => {
               console.log(`Server says: ${event.data}`);
           });

           // Connection closed
           socket.addEventListener('close', (event) => {
               console.log('Connection closed');
           });

           // Clean up the WebSocket connection on component unmount
           return () => {
               socket.close();
           };
       }, []); // Empty dependency array ensures the effect runs once on mount

       return (
           <div>
               <p>WebSocket communication with React</p>
           </div>
       );
   };

   export default WebSocketExample;
   ```

 