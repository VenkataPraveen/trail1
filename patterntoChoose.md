# How to choose a design Pattern?

| Scenario | Design Pattern |
|----------|----------------|
| Need to create an object without specifying the exact class | Factory Method |
| Need to ensure a class has only one instance | Singleton |
| Need to build a complex object step by step | Builder |
| Need to provide a simplified interface to a complex system | Facade |
| Need to add responsibilities to objects dynamically | Decorator |
| Need to allow an object to alter its behavior when its internal state changes | State |
| Need to define a family of algorithms and make them interchangeable | Strategy |
| Need to provide a way to access elements of a collection sequentially without exposing its underlying representation | Iterator |
| Need to define the skeleton of an algorithm, deferring some steps to subclasses | Template Method |
| Need to allow an object to notify other objects about changes in its state | Observer |

Ex: Double Entry book keeping 

## What is the Problem Space

When choosing a design pattern, it's essential to understand the problem space you are dealing with. The problem space refers to the specific context and requirements of the problem you are trying to solve. By clearly defining the problem space, you can more effectively select the appropriate design pattern that addresses the specific needs and constraints of your situation.

Consider the following aspects when defining the problem space:
- The nature of the problem: Is it related to object creation, structure, or behavior?
- The specific requirements and constraints: What are the key factors that need to be addressed?
- The desired outcomes: What are the goals you aim to achieve with the solution?

By thoroughly analyzing the problem space, you can make a more informed decision on which design pattern to apply, ensuring a more effective and efficient solution.

## Types of Design Patterns

Design patterns can be broadly categorized into three types:

1. **Creational Patterns**: These patterns deal with object creation mechanisms, trying to create objects in a manner suitable to the situation. The basic form of object creation could result in design problems or added complexity to the design. Creational design patterns solve this problem by controlling the object creation process. Examples include:
    - Factory Method
    - Abstract Factory
    - Singleton
    - Builder
    - Prototype

2. **Structural Patterns**: These patterns deal with object composition or the way to realize relationships between entities. They help ensure that if one part of a system changes, the entire system doesn't need to change along with it. Examples include:
    - Adapter
    - Composite
    - Proxy
    - Flyweight
    - Facade
    - Bridge
    - Decorator

3. **Behavioral Patterns**: These patterns are concerned with algorithms and the assignment of responsibilities between objects. They help in defining how objects interact and communicate with each other. Examples include:
    - Strategy
    - Observer
    - Command
    - Iterator
    - Mediator
    - Memento
    - State
    - Template Method
    - Visitor
    - Chain of Responsibility

Understanding these categories can help you identify the right pattern to use based on the specific problem you are trying to solve.


## Event-Driven Pattern

The Event-Driven pattern is a design pattern in which the flow of the program is determined by events such as user actions, sensor outputs, or messages from other programs or threads. This pattern is particularly useful in applications that require a high level of interaction or real-time processing.

### When to Use the Event-Driven Pattern

Consider using the Event-Driven pattern in the following scenarios:
- When you need to decouple event producers from event consumers.
- When you need to handle asynchronous events or messages.
- When you need to implement a system that reacts to a variety of events in real-time.
- When you need to improve the scalability and responsiveness of your application.

### Key Components

1. **Event Source**: The component that generates events. This could be user actions, system events, or messages from other systems.
2. **Event Listener**: The component that listens for and processes events. Listeners are typically registered with event sources.
3. **Event Bus**: An optional component that acts as an intermediary, dispatching events from sources to listeners.

### Examples

- **User Interface Applications**: GUI applications often use event-driven patterns to handle user interactions such as clicks, key presses, and mouse movements.
- **Real-Time Systems**: Systems that require immediate processing of events, such as monitoring systems or financial trading platforms.
- **Microservices Architecture**: Event-driven patterns are commonly used in microservices to handle communication between services asynchronously.

By incorporating the Event-Driven pattern, you can create systems that are more modular, responsive, and easier to maintain.


## Is Event-Driven Pattern Part of the Three Main Categories?

The Event-Driven pattern is not strictly categorized under the traditional three types of design patterns: Creational, Structural, and Behavioral. Instead, it is often considered a broader architectural pattern that can encompass elements of all three categories depending on its implementation.

### How Event-Driven Pattern Relates to Other Patterns

- **Creational**: Event-driven systems may use creational patterns like Singleton or Factory Method to manage the creation of event sources or listeners.
- **Structural**: Structural patterns like Adapter or Facade can be used to integrate event-driven components with other parts of a system.
- **Behavioral**: Many behavioral patterns, such as Observer, Mediator, or Command, are inherently event-driven as they deal with communication and interaction between objects.

While the Event-Driven pattern itself is not confined to a single category, it often leverages various design patterns to achieve its goals. This makes it a versatile and powerful approach for designing complex, interactive, and scalable systems.


## Other Useful Patterns in Software Architecture

Apart from the traditional Creational, Structural, and Behavioral design patterns, there are several other patterns that are highly useful in software architecture development. These patterns address various aspects of software design and can help in creating robust, scalable, and maintainable systems.

### Architectural Patterns

1. **Layered (n-tier) Pattern**: This pattern organizes the system into layers with each layer performing a specific role within the application. Common layers include presentation, business logic, and data access layers.
2. **Microservices Pattern**: This pattern structures an application as a collection of loosely coupled services, each implementing a specific business capability. It promotes scalability and ease of deployment.
3. **Event-Driven Architecture**: This pattern uses events to trigger and communicate between decoupled services. It is highly suitable for applications that require high scalability and real-time processing.
4. **Serverless Architecture**: This pattern involves building and running applications without managing the infrastructure. It allows developers to focus on code while the cloud provider handles the server management.
5. **Service-Oriented Architecture (SOA)**: This pattern involves designing software systems as a collection of services that communicate over a network. Each service is a discrete unit of functionality.

### Concurrency Patterns

1. **Thread Pool Pattern**: This pattern manages a pool of worker threads to perform tasks concurrently, improving resource utilization and performance.
2. **Producer-Consumer Pattern**: This pattern separates the work of producing data from the work of consuming data, allowing both to operate concurrently.
3. **Reactor Pattern**: This pattern handles service requests that are delivered concurrently to an application by one or more clients.

### Integration Patterns

1. **Adapter Pattern**: This pattern allows incompatible interfaces to work together by converting the interface of a class into another interface that clients expect.
2. **Bridge Pattern**: This pattern decouples an abstraction from its implementation, allowing the two to vary independently.
3. **Proxy Pattern**: This pattern provides a surrogate or placeholder for another object to control access to it.

### Security Patterns

1. **Singleton Pattern**: Ensures a class has only one instance and provides a global point of access to it, often used in managing shared resources.
2. **Proxy Pattern**: Can be used to control access to sensitive objects by providing a surrogate or placeholder.
3. **Chain of Responsibility Pattern**: Allows an object to pass a request along a chain of potential handlers, useful in implementing authentication and authorization mechanisms.

By understanding and applying these additional patterns, you can enhance the architecture of your software systems, making them more adaptable, scalable, and easier to maintain.
