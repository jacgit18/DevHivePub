---
tags:
  - formats
  - Serialization
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses message formats and originated from a medium article.
Status: Done
Started: 2024-03-03
EditDate: 
Relates: 
Peer Reviewed: 0
dg-publish:
---
Message formats go hand in hand with communication protocols; They describe in-wire format of the message being sent. They usually broken down into two types human readable and non-human readable. Examples are XML, JSON and [protocol buffers](https://youtu.be/46O73On0gyI).

When a client sends a message to a backend, it needs to serialize the message from the language data structure to the on-wire message format. When the backend receives the message it needs to then deserialize the message from this format to the language data structure.

That is why it is absoluity fine to have a Javascript client communicates with a C# backend using JSON as a message format. The native JSON object of javascript will be converted to a JSON byte string in the wire, the C# backend then deserializes the byte string to a C# structure representing a dictionary. It is important to understand the cost associated with serializing and deserializing message format.

XML was one of the original message formats designed to be human-readable. However, computers had difficulty dealing with XMLs, so protocol buffers format was created to make the message format smaller and more friendly. Protocol buffers became very popular and were designed to solve the problem of high bandwidth messages. Protocol buffers minimize the payload so fewer bytes can be sent. It also speeds up the serialization and deserialization process.

Becoming specialized in message formats is also an option. You may invent the next message format that may become the standard to serve us for the next 50 years.



