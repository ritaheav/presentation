# presentation-Q3-2019  
My name is Margharyta Niabesnaya.  
###### (Slide - Asynchronous Javascript)  
I want to talk about asynchronous javascript, because we often need to deal with asynchronous behavior, which can be confusing for programmers. This presentation will explain what asynchronous code is. But the first, I think, we must consider what is Synchronous Code.   
###### (Slide - Synchronous Javascript)  
In a synchronous programming model, things happen one at a time. When you call a function that performs a long-running action, it returns only when the action has finished and it can return the result. This stops your program for the time the action takes. Which means for example we have 2 lines of codes Line-1 followed by Line-2. Synchronous means Line-2 can not start running until the Line-1 has finished executing.  
###### (Slide - Stack)  
JavaScript is single-threaded, that means only one statement is executed at a time, so it has a single call stack. The call stack is used to store all the execution context created during the code execution. The call stack has a LIFO structure which means that the items can be added or removed from the top of the stack only. And an Execution Context is an abstract concept of an environment where the JavaScript code is evaluated and executed.   
###### (Slide - Example of synchronous javascript)  
So let's see the example:  
Step 1: The console.log("Print 1") is pushed into the call stack and executed, once done with execution, it is then popped out of the stack. Now the stack is empty and ready for any next instruction to be executed.  
Step 2: console.log("Print 2") is the next instruction is pushed and the same thing repeats until - Step 3: is executed and there is nothing left to push and execute.  
Asynchronous model  
###### (Slide - Asynchronous code)  
Synchronous executions of code may seem straightforward but can be slow. For example, tasks like image processing, file operations making network request and waiting for response. So this things in Call stack results in “Blocking”. When call stack is blocked, the browser prevents user’s interrupts and other code statements from executing until the blocking statement is executed and the call stack is freed. Therefore Asynchronous callbacks are used to handle such situations.  
###### (Slide - setTimeout function)  
Well the function setTimeout() is probably the simplest and easiest way to demonstrate asynchronous behaviour.  
###### (Slide - Example of setTimeout function)  
at Step 1: As usual console.log("Hello ") gets pushed into the stack first and is executed then popped out when done.  
Step 2: setTimeout() gets pushed into the stack, but Note- console.log("Siddhartha") cannot be executed (or pushed to the stack) immediately because it is meant to execute in some future time (about after 2 seconds). So it disappears for now.  
Step 3: Naturally next line console.log(" I am ") is pushed into the stack, gets executed and is popped out immediately.  
Step 4: Call stack is empty and waiting.  
Step 5: Suddenly console.log( "Siddhartha" ) is found pushed into the stack after 2 seconds as setTimeout() has timed out. It is then executed and once done is popped out of the Stack at Step 6: Stack is empty again.  
###### (Slide - Explain example of the setTimeout function)  
So lets try to figure out what happened to the setTimeout().   
First we look at what is an event loop. The job of the Event loop is to look into the call stack and determine if the call stack is empty or not. If the call stack is empty, it looks into the message queue to see if there’s any pending callback waiting to be executed. In this case, the message queue contains one callback, and the call stack is empty at this point. So the Event loop pushes the callback to the top of the stack.  
Step 2: At this point setTimeout gets pushed into the call stack. As we can see it has to components a callback and a delay of 2 s. Now setTimeout() is not a part of any JavaScript engine, it’s in fact, a Web API included in the browser environment as an extra feature.  
Step 3: So the browser Web API takes responsibility of the callback provided and fires up the timer of 2000 ms leaving behind setTimeout() statement which has done its job, so is popped out of the stack.   
Step 4: The next line in our script console.log( "I am" ) is pushed into the stack and popped out after its execution.  
Step 5: Now we have a callback in the WebAPIs which is going to get triggered after 2 s. But WebAPIs directly can not PUSH things randomly into the call-stack, because it might create an interrupt to some other code being executed by the JavaScript engine at that moment. So instead the callback is inserted into the Callback Queue/Task Queue after the timer of 2 s over. WebAPI is now empty and freed.  
Step 6: Event Loop — it is responsible for taking out the first element from the Callback/Task Queue and PUSH it into the Call-Stack only when the stack is empty or free, so at this point of our equation, the Call-Stack is empty.  
Step 7: So callback is pushed into the Call-Stack from the Callback/Task queue by the Event Loop , and callback is executed.   
Step 8: So another executable statement console.log("Siddhartha") is found inside the callback ‘s scope, therefore console.log("Siddhartha") is pushed into the Call-Stack.  
Step 9: Once console.log("Siddhartha") is executed, it is then popped out of the Call-Stack, and JavaScript engine comes back to finish executing the callback ‘s remaining body. Which when done, callback is popped out of the Call-Stack.  
###### (Slide - Promises)  
Promises.  
###### (Slide - States of promises)  
A promise is an object which can be returned synchronously from an asynchronous function. A promise may be in one of 3 possible states: fulfilled, rejected, or pending.  
###### (Slide - promises example)  
The main advantage of promises—they simplify the use of asynchronous functions. Instead of having to pass around callbacks, promise-based functions look similar to regular ones: they take input as arguments and return their output. The only difference is that the output may not be available yet.  
Microtasks.  
###### (Slide - Microtasks)  
Microtasks are usually scheduled for things that should happen straight after the currently executing script. The microtask queue is processed after callbacks as long as no other JavaScript is mid-execution, and at the end of each task.  
###### (Slide - Microtasks example)  
Once a promise settles, or if it has already settled, it queues a microtask for its reactionary callbacks. This ensures promise callbacks are async even if the promise has already settled. So calling .then against a settled promise immediately queues a microtask. This is why promise1 and promise2 are logged after script end, as the currently running script must finish before microtasks are handled. promise1 and promise2 are logged before setTimeout, as microtasks always happen before the next task.  
Summary.  
###### (Slide - Summary)  
Asynchronous programming makes it possible to express waiting for long-running actions without freezing the program during these actions.   
Programming asynchronously is made easier by promises, objects that represent actions that might complete in the future, and async functions, which allow you to write an asynchronous program as if it were synchronous.  



