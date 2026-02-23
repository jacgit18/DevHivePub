---
tags:
  - multiThreading
author:
  - jacgit18
  - chatgpt
Purpose: This documentation discusses process and threads
Status: Refinement
Started: 
EditDate: 2024-03-05
Relates: 
Peer Reviewed: 0
dg-publish:
---
Process
Instance of a program/application
Has resources such as memory, etc.
Has at least one thread


Thread
Sequence of programmed instructions
The thing that executes a program's code
Utilizes process resources

"Single-threaded" means that we open a single connection and measure the speeds from that. "Multi-threaded" means that we're using multiple connections - usually anywhere from 3 to 8 - at the same time, and measure the total speed across them all. 

Registers are used by the CPU when it's currently running a particular thread. When the OS decides to switch from one thread to another, the OS saves the current values of all the register into a private memory area specific to the first thread.

"There isn't a direct way to stop a thread in Java. Often, you have to wait for a thread to die when it finishes executing. If you need to manually kill a thread, you can use a Volatile boolean variable within a thread that throws an exception when triggered from another thread."

Each parent thread Can have up to 4 Child thread  running concurrently 
![[Concurrencey.jpg]]


Multithreading is used to run things in Parallel or Parallel Processing


```Java


class Adder (
private String inFile, outFile;
public Adder(String inFile, String outFile) {/* assign filenames to member fields */ }
public void doAdd() throws IOException (
int total = 0;
String line = null;
try (BufferedReader reader = Files.newBufferedReader(Paths.get(inFile))) {
while ((line = reader.readLine()) != null)
total += Integer.parseInt(inline);
}
try (BufferedWriter writer = Files.newBufferedWriter(Paths.get(outFile))) {
writer.write("Total: " + total);
		}
	}
}



```

![[Adder classes.jpg]]

## single thread usage
![[Using Adder classes.jpg]]

![[Process on single thread.jpg]]

**Main thread waits for other threads
![[Processing on multi thread.jpg]]

## Thread foundation type 

Runnable interface
- Represents a task to be run on a thread  
- only member is the run method
![[Adder with thread.jpg]]


Thread class
- Represented a thread of execution  
- Can interact with and effect thread state  
- Begin execution with start method

![[Running Adder on thread.jpg]]

```Java 

String[] inFiles = ("./file1.txt"
String[] outFiles = ("./file1.out.txt"
"./file6.txt");
./file6.out.txt");
Thread[] threads = new Thread[inFiles.length];
for(int i=0; i < inFiles.length; i++) (
Adder adder = new Adder(inFiles[i], outFiles[i]);
threads[i] = new Thread(adder);
threads[i].start();
for (Thread thread:threads)
thread.join(); // Blocks waiting for thread completion
```


![[Running Adder on thread Blocks.jpg]]

## Thread pool type  
  [[Thread pools]]
  
ExecutorService interface  
- Models thread pool behavior 
- Can submit tasks  
- Request and wait for pool shutdown  
  
  
  
Executors class  
- Methods for creating thread pools
- Dynamically sized pools  
- Size limited pools  
- Pools that schedule tasks for later




![[Thread pool.jpg]]

## Threading relationship Types 

### Callable interface
Represents a task to be run on a thread
Can return results
Can throw exceptions
Only member is the call method


### Future interface
Represents results a thread task
Returned by ExecutorService.submit
The key method is get
Blocks until task completes
Returns Callable interface result
Throws Callable interface exception