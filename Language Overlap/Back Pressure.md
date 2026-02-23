---
tags:
  - asynchronous
  - synchronous
  - architecturalParadigm
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses back pleasure.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: "[[Asynchronous Programming]]"
Peer Reviewed: 0
dg-publish:
---
**Understanding Back Pressure in Asynchronous Programming and Reactive Systems**

Back pressure is a fundamental concept within the realm of asynchronous programming and reactive systems. It serves as a critical mechanism for addressing scenarios where a downstream component or subscriber becomes overwhelmed by the influx of data from an upstream source, making it unable to process this data as quickly as it's being generated. This imbalance can lead to issues such as memory overflow and a decrease in system performance. To tackle these challenges, back pressure mechanisms come into play, allowing the downstream component to signal the upstream source to slow down or momentarily halt data production. This ensures a smoother and more efficient flow of information.

To manage back pressure effectively, systems often employ buffers or queues to temporarily store surplus events or data until the system can catch up. Reactive frameworks such as RxJava, Project Reactor, and Akka Streams frequently come equipped with built-in tools for handling back pressure, making it more manageable.

> [!info] 
> Back pressure is less relevant in synchronous code since execution is typically blocking, and the producer will wait for the consumer to process the data.

While back pressure is a concept deeply rooted in reactive programming, it can also prove valuable in event-driven architectures, especially when designing systems that depend on asynchronous communication and need to manage varying rates of event generation and consumption.

**Implementing Back Pressure in Java with Project Reactor**

In Java, especially when using reactive programming frameworks like Project Reactor or RxJava, you can implement back pressure effectively. Let's illustrate this with an example using Project Reactor:

```java
import reactor.core.publisher.Flux;
import reactor.core.scheduler.Schedulers;

public class BackpressureExample {

    public static void main(String[] args) throws InterruptedException {
        Flux<Integer> source = Flux.range(1, 1000)
                .onBackpressureBuffer(10)
                .publishOn(Schedulers.parallel());

        source.subscribe(
                data -> {
                    // Simulate a slow subscriber
                    try {
                        Thread.sleep(100);
                    } catch (InterruptedException e) {
                        e.printStackTrace();
                    }
                    System.out.println("Received: " + data);
                },
                Throwable::printStackTrace,
                () -> System.out.println("Done")
        );

        Thread.sleep(10000);
    }
}
```

In this example, the `onBackpressureBuffer(10)` method is used to buffer up to 10 items when the downstream (subscriber) lags behind the upstream (publisher), preventing an overwhelming situation.

**Implementing Back Pressure in TypeScript with RxJS**

For TypeScript and RxJS, you can also implement back pressure. Here's a simple example using the `bufferCount` operator:

```javascript
const { interval, Subject } = require('rxjs');
const { bufferCount, mergeMap } = require('rxjs/operators');

// Create a subject to simulate an observable source
const source = new Subject();

// Simulate a fast producer (emitting values every 100 milliseconds)
const producer = interval(100).subscribe(value => source.next(value));

// Simulate a slower consumer (processing batches of 5 values every 500 milliseconds)
const consumer = source.pipe(
  bufferCount(5), // Buffer incoming values into arrays of size 5
  mergeMap(batch => {
    // Simulate asynchronous processing
    return new Promise(resolve => {
      setTimeout(() => {
        console.log('Processed batch:', batch);
        resolve();
      }, 500);
    });
  })
).subscribe();

// Simulate the application running for 5 seconds
setTimeout(() => {
  // Unsubscribe to stop the simulation
  producer.unsubscribe();
  consumer.unsubscribe();
}, 5000);
```

In this example:

1. `interval(100)` simulates a fast producer emitting values every 100 milliseconds.
2. `bufferCount(5)` buffers incoming values into arrays of size 5, effectively controlling the flow.
3. `mergeMap` is used to simulate asynchronous processing of each batch.
4. The `setTimeout` is used to run the simulation for 5 seconds before unsubscribing from both the producer and consumer.

This example shows how backpressure can be managed by buffering values and controlling the rate of consumption. Adjust the interval and buffer size based on your specific requirements.

### More complex Example


```java  
import reactor.core.publisher.Flux;  
import reactor.core.scheduler.Schedulers;  
  
public class BackPressureExample {  
  
public static void main(String[] args) {  
// Create a Flux emitting elements from 1 to 1000  
Flux<Integer> numbersFlux = Flux.range(1, 1000);  
  
// Simulate a slow subscriber (e.g., heavy computation, network call)  
numbersFlux  
.publishOn(Schedulers.single()) // Simulate work on a separate scheduler  
.doOnNext(i -> simulateWork()) // Simulate work for each element  
.subscribe(  
BackPressureExample::processData,  
BackPressureExample::handleError,  
BackPressureExample::handleComplete  
);  
  
// Sleep to allow the subscription to demonstrate back pressure  
sleep(5000);  
}  
  
private static void processData(int data) {  
System.out.println("Received: " + data);  
}  
  
private static void handleError(Throwable throwable) {  
System.err.println("Error: " + throwable.getMessage());  
}  
  
private static void handleComplete() {  
System.out.println("Processing completed");  
}  
  
private static void simulateWork() {  
// Simulate some heavy computation or network call  
sleep(50);  
}  
  
private static void sleep(long milliseconds) {  
try {  
Thread.sleep(milliseconds);  
} catch (InterruptedException e) {  
Thread.currentThread().interrupt();  
}  
}  
}  
```  
In this example:  
  
- We create a Flux emitting integers from 1 to 1000.  
- We simulate a slow subscriber by using the `publishOn` operator to perform work on a separate scheduler and `doOnNext` to simulate work for each element.  
- The subscriber (in the `subscribe` method) is set up to process data, handle errors, and complete.  
- The `simulateWork` method simulates some heavy computation or network call.  
- We use a `sleep` method to allow the subscription to run for a certain period, demonstrating back pressure.  

`BackPressureExample::processData`, represents a method reference. [[Static Method Reference |Method references]] are a shorthand way to refer to a method as a lambda expression for specific contexts, particularly when working with functional interfaces. In your example, `BackPressureExample::processData` accomplishes the following:

1. **Reference to a Method:** It refers to the `processData` method of the `BackPressureExample` class.

2. **Functional Interface Context:** Method references are often used when you have a functional interface, which is an interface with a single abstract method (SAM). In your case, it's likely being used as an argument to the `subscribe` method of a Flux or Observable.

   For example, if you have a functional interface like `Consumer<T>`, which has a single abstract method `accept(T t)`, you can use a method reference to match the method's signature:

   Here, `BackPressureExample::processData` is a shorthand for creating a `Consumer` that accepts an integer and calls the `processData` method with that integer.

So, in the context of your code, `BackPressureExample::processData` is used as a callback or action to be executed for each element emitted by the `numbersFlux`. When an item is emitted, it will call the `processData` method, passing the emitted item as an argument.

This is a more concise and readable way to specify the behavior without writing a full lambda expression or anonymous inner class. It simplifies the code and makes it more expressive when working with functional programming constructs like Reactor's `Flux` and Java's functional interfaces.

This is a basic example, and in a real-world scenario, you might encounter back pressure handling in more complex situations where data is generated at a high rate, and the consumer needs to signal the producer to slow down. Reactive Streams provides a standard for handling back pressure, and libraries like Project Reactor implement this standard.


```typescript
import { of, Observable } from 'rxjs';
import { tap, subscribeOn } from 'rxjs/operators';

function processData(data: number) {
  console.log("Received: " + data);
}

function handleError(throwable: any) {
  console.error("Error: " + throwable.message);
}

function handleComplete() {
  console.log("Processing completed");
}

function simulateWork() {
  // Simulate some heavy computation or network call
  sleep(50);
}

function sleep(milliseconds: number) {
  return new Promise(resolve => setTimeout(resolve, milliseconds));
}

const numbersObservable = of(...Array.from({ length: 1000 }, (_, i) => i + 1));

numbersObservable
  .pipe(
    subscribeOn(asyncScheduler), // Simulate work on a separate scheduler
    tap(i => simulateWork()) // Simulate work for each element
  )
  .subscribe(
    processData,
    handleError,
    handleComplete
  );

const asyncScheduler = new Observable<number>(subscriber => {
  (async () => {
    await sleep(5000);
    subscriber.complete();
  })();
});
```



In summary, both Java with Project Reactor/RxJava and TypeScript with RxJS provide mechanisms for handling backpressure, and you can choose strategies like buffering to control the flow of events in reactive systems.