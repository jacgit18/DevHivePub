---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - architecturalPatterns
  - eventDriven
  - coupling
  - events
  - asynchronous
  - scalability
  - synchronous
  - microservices
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Event Driven Architecture.
Status: Refinement
Started: null
EditDate: 2024-03-07T00:00:00.000Z
Relates: null
Peer Reviewed: 0
dg-publish: null
---
![[Event Driven Architecture]]

Event-Driven Architecture (EDA) is a software design pattern is an alternative to request response architecture found in REST or gRPC. It focuses on the generation, detection, consumption,  and response to events and event-driven messages within a system. In EDA, the flow of data and the triggering of actions are driven by events, which are occurrences or changes in the system or external environment. This architectural approach is widely used in modern software systems to create scalable, decoupled, and responsive applications that has an effective communication and coordination among different components of a system. Here are some key concepts and components of Event-Driven Architecture:

1. **Event:**
   - An event is a significant occurrence or change in a system that can be captured and processed. Events can represent a wide range of activities, such as user interactions, system alerts, sensor data, or application state changes.
   - Events are immutable facts that have already occurred. They describe something that has happened in the past and are used to communicate changes in the system.

2. **Event Source:**
   - An event source is an entity or component that generates events. Event sources can include user interfaces, IoT devices, databases, application services, and external systems.

3. **Event Broker/Message Broker:**
   - An event broker (or message broker) is a central component that manages the distribution of events. It acts as an intermediary between event sources and event consumers, ensuring that events are delivered to the right recipients. Popular event brokers include Apache Kafka, RabbitMQ, and AWS EventBridge.

4. **Event Consumer:**
   - An event consumer is a component that subscribes to and processes events from the event broker. Consumers can be applications, services, or microservices that react to specific events by executing business logic.
   
5. **Event Producers:**
   - Event producers are components or services responsible for generating and emitting events. These can include user interfaces, microservices, sensors, or any part of the system capable of triggering events.

6. **Event Handler:**
   - An event handler is a piece of code or a function that processes a specific type of event. Event handlers are responsible for taking appropriate actions in response to an event, such as updating data, sending notifications, or triggering other events.

7. **Asynchronous Communication:**
   - EDA often relies on asynchronous communication, meaning that event producers and consumers do not need to be available or active at the same time. This decoupling allows for better scalability and fault tolerance.

8. **Loose Coupling:**
   - EDA promotes loose coupling between components, as events act as a contract between producers and consumers. Producers do not need to be aware of who will consume their events, and consumers do not need to know the source of the events they receive.

9. **Scalability and Resilience:**
   - EDA supports horizontal scalability, as you can add more event consumers to handle increased event loads. It also enhances system resilience because a failure in one part of the system does not necessarily disrupt the entire process.

10. **Event Sourcing:**
   - Event Sourcing is a related pattern where the state of an application is derived from a sequence of immutable events. This is often used in systems where auditing, history tracking, and undo/redo functionality are important.

11. **Pub-Sub Model:**
   - EDA can be implemented using a Publish-Subscribe (Pub-Sub) model, where event producers publish events to specific topics or channels, and event consumers subscribe to these topics to receive relevant events.

> [!info] 
> An interesting aspect is that event-driven architecture can be integrated into various architectural styles, including microservices.

## Event Bus and Broker

An event bus and broker are similar in the sense that they both facilitate the communication and exchange of information between different components or services in a system. However, they are not exactly the same, and there are some distinctions between the two:  
  
**Event Bus**:  
1. **Communication Model**: An event bus is a communication model or pattern that focuses on one-to-many communication. It allows multiple components to publish events, and other components can subscribe to receive those events.  
2. **Decoupling**: Event buses are often used to create loose coupling between components. Publishers and subscribers don't need to be aware of each other's existence.  
3. **Event Types**: Events on an event bus are typically categorized by types or topics, and subscribers express interest in specific event types.  
4. **Synchronous or Asynchronous**: Event buses can be implemented synchronously or asynchronously, depending on the system's needs.  
  
**Message Broker**:  
1. **Middleware**: A message broker is a specific piece of middleware or software that acts as an intermediary for routing, storing, and managing messages.  
2. **One-to-One and One-to-Many**: While message brokers can facilitate one-to-many communication, they are often used for both one-to-one and one-to-many communication. Messages can be directed to specific recipients (point-to-point) or broadcast to multiple consumers (publish-subscribe).  
3. **Guaranteed Delivery**: Message brokers often provide mechanisms for guaranteed message delivery, even if some components are temporarily unavailable.  
4. **Queues and Topics**: Message brokers typically support both queues (point-to-point) and topics (publish-subscribe) for message distribution. 


It's important to note that Event-Driven Architecture is not tied to specific technologies such as microservices, serverless, or streaming. Instead, it represents a design paradigm that focuses on handling and responding to events and messages in a decoupled and asynchronous manner. The implementation of EDA can be achieved using a variety of tools, frameworks, and architectural patterns.

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠==


# Excalidraw Data

## Text Elements
## Embedded Files
9aaa930e9ae1677999d8b205df69c4231a269848: [[Event Driven Arch Solution.png]]

%%
## Drawing
```compressed-json
N4KAkARALgngDgUwgLgAQQQDwMYEMA2AlgCYBOuA7hADTgQBuCpAzoQPYB2KqATLZMzYBXUtiRoIACyhQ4zZAHoFAc0JRJQgEYA6bGwC2CgF7N6hbEcK4OCtptbErHALRY8RMpWdx8Q1TdIEfARcZgRmBShcZQUebQB2bQAWGjoghH0EDihmbgBtcDBQMBKIEm4IABk2YgA1AFYg4lSSyFhECsJ9aKR+UsxuZx54gAZtAGZxkfiATgA2HnqeGeHx

+L7IGEHhuPGeAA4ARkWNiAoSdW56mfHtQ7nD68WR+v36pPXCyEkEQmVpbhJPbaGb1eI8OZJUHgyGg07WZTBbgjU7MKCkNgAawQAGE2Pg2KQKujrMw4LhAtkWqVNLhsJjlBihBxiHiCUSJCSOGSKVkoNTIAAzQj4fAAZVgSIkkjpGkCAogaIx2IA6hdJNxDqj0ViEBKYFL0IIPAqmf8OOFcmgtV8IGxydg1FtrSMUbamSyLcwragOEJRaiEAhmmgH

jMjqdGCx2FxQ3NI0xWJwAHKcMSa2bjJJJQ4w05CODEXBQYMZ8b1SE8KbTEb7U6EZgAEXSJZDqEFBDCp0ZwjgAEliD68gBdU6aYQsgCiwUy2SHo9tRA4mO4foDi7Y9NLaA7+C7tuFwQHFRmuDPNxGCFPCHu8VmMxmxH2mh4L2IgrmM2wSSrh1wEPDJJ9gVZh3HEVAClaMAbSgw4vgXVoyhZLAKlwEYFUFchMmPNA13wbViyEH0IEQFlCA4ZQFWwDE

4FXf18EKABfcAEIgXA4DgCVi3A4o2h+TIKiIf5+T6BhCAQCgACE6QZD1WXxQkKgAYkFVS1OpCBsBESkoD7Et9AlZVcQUjl0CUw4b0sjStNIHS9IyaT6R7Zl5PZYlyG5ckdOs7S+Xs/QADERXFSVwMVfFylEmy7P0wzdTVYhLjQPhCk03zsn8uLsX1Q1wpNKL0t0/SACVhHNS1NQK2y/P0gB5B0nU1V0qpijIAs4KAAtwfQRWdVAYMgaKarajqxUI

IxwNfFrhv0AAVLAoAAQSE2N0GCQURNSoaMtiqJSCW2y2AoH5cDbPDpp2jJJxZRbDuOkI2zYu6fOqy79FujEKFm+AwrkjTQIxUUAA1uAOeoQSSEZsxGNZM3DeNUoB/F8AATW4GZ7gSBZ9jmcs9k/BZRKMNgDG4XjIHoAghHAw5tBGT8XhmJiLqKjJSpcr1iL+0TGRIMaJtBt1Sl54gJQQWi0HqHnSBIABZGoEGu3BNGCNtd33YWZdcxS0HJiBJPxR

6lJxGYTZNgKAoVYqEGUf0KWUydG0dx2LYgZmtsKrKEHqqAYx9c7Usw7qEGt5CZYosnbSyZXVe4dFqdObAiAl1B44QU4OGDuPSAT21hCgJdwLT93SjsAArBBsByMVM7geXiEVzOVe3dtO3T1K6V9xhZpJ/BI8Q9owrCYIq5jKiiKgAxvo6XD6NOAktzVtv59CJbR+73u6NFJjwEY/gIEPcIyeYxigA===
```
%%