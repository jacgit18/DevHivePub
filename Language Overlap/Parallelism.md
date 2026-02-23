---
tags:
  - parallelProcesses
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Parallelism
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class ParallelismExample {
    public static void main(String[] args) {
        // Creating an ExecutorService with a fixed thread pool
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Submitting tasks for parallel execution
        executorService.submit(() -> performTask("Task 1"));
        executorService.submit(() -> performTask("Task 2"));
        executorService.submit(() -> performTask("Task 3"));

        // Shutting down the ExecutorService
        executorService.shutdown();

        try {
            // Waiting for all tasks to complete or timeout after 5 seconds
            executorService.awaitTermination(5, TimeUnit.SECONDS);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("All tasks completed!");
    }

    // Example task
    private static void performTask(String taskName) {
        System.out.println("Starting " + taskName);
        // Simulating some computation
        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println(taskName + " completed");
    }
}

```










```javascript
// Creating new web workers
const worker1 = new Worker('worker.js');
const worker2 = new Worker('worker.js');
const worker3 = new Worker('worker.js');

// Handling messages from the workers
worker1.onmessage = function(event) {
  console.log('Worker 1 result:', event.data);
};

worker2.onmessage = function(event) {
  console.log('Worker 2 result:', event.data);
};

worker3.onmessage = function(event) {
  console.log('Worker 3 result:', event.data);
};

// Starting parallel tasks
worker1.postMessage(10);
worker2.postMessage(20);
worker3.postMessage(30);
```



```javascript
// Handling messages from the main script
self.onmessage = function(event) {
  const data = event.data;
  console.log('Received data:', data);

  // Perform some computation
  const result = processData(data);

  // Send the result back to the main script
  self.postMessage(result);
};

// Example computation function
function processData(data) {
  // Perform computation on data
  const result = data * 2;

  // Simulating some delay
  const startTime = Date.now();
  while (Date.now() - startTime < 2000) {}

  return result;
}
```

In this example, we create three web workers (`worker1`, `worker2`, and `worker3`) by instantiating the `Worker` object and providing the URL of the worker script (`worker.js`). The worker script contains the computation logic.

The `onmessage` event handlers in the main script listen for messages sent by the workers. Each worker performs its computation by receiving the data from the main script, executing the `processData` function, and sending the result back to the main script using `self.postMessage()`.

When you run the code, the main script will create three web workers and send different data values to each worker. Each worker will perform the computation in parallel and send the result back to the main script. The main script will log the received results from each worker.

Web workers allow parallelism in JavaScript by executing code in separate threads, allowing tasks to be performed concurrently. In this example, the web workers run in parallel, and the computations carried out by each worker can occur simultaneously, utilizing the available CPU cores.