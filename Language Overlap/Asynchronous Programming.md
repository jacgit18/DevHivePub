---
tags:
  - asynchronous
  - concurrency
  - codeExecution
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses Asynchronous programming.
Status: Done
Started: 
EditDate: 2024-03-04
Relates: 
Peer Reviewed: 0
dg-publish: true
---
Asynchronous programming allows tasks to be executed independently and concurrently. It doesn't block the execution of the program, enabling multiple operations to be performed simultaneously. This approach is particularly useful when dealing with I/O operations or time-consuming tasks.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.TimeUnit;

public class AsynchronousExample {

    public static void main(String[] args) {
        System.out.println("Start");

        // Task 1
        CompletableFuture<Void> task1Future = CompletableFuture.runAsync(AsynchronousExample::task1);

        // Task 2
        CompletableFuture<Void> task2Future = CompletableFuture.runAsync(AsynchronousExample::task2);

        // Wait for both tasks to complete
        CompletableFuture.allOf(task1Future, task2Future)
                .thenRun(() -> {
                    System.out.println("End");
                })
                .join();
    }

    private static void task1() {
        System.out.println("Executing Task 1");
        // Simulate time-consuming operation
        try {
            TimeUnit.SECONDS.sleep(2);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("Task 1 completed");
    }

    private static void task2() {
        System.out.println("Executing Task 2");
        // Simulate time-consuming operation
        try {
            TimeUnit.SECONDS.sleep(1);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("Task 2 completed");
    }
}

```



```javascript 
console.log("Start");

// Task 1
const task1Promise = new Promise((resolve, reject) => {
    console.log("Executing Task 1");
    // Perform some time-consuming operation
    setTimeout(() => {
        console.log("Task 1 completed");
        resolve();
    }, 2000);
});

// Task 2
const task2Promise = new Promise((resolve, reject) => {
    console.log("Executing Task 2");
    // Perform some time-consuming operation
    setTimeout(() => {
        console.log("Task 2 completed");
        resolve();
    }, 1000);
});

// Wait for both promises to resolve
Promise.all([task1Promise, task2Promise]).then(() => {
    console.log("End");
});

```

## Output 
>  Start
Executing Task 1
Executing Task 2
Task 2 completed
Task 1 completed
End




