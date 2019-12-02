presentation-Q3-2019
My name is Margharyta Niabesnaya.
(Slide - Asynchronous Javascript)
I want to talk about asynchronous javascript, because we often need to deal with asynchronous behavior, which can be confusing for programmers. This presentation will explain what asynchronous code is. But the first, I think, we must consider what is Synchronous Code. 
(Slide - Synchronous Javascript)
In a synchronous programming model, things happen one at a time. When you call a function that performs a long-running action, it returns only when the action has finished and it can return the result. This stops your program for the time the action takes. Which means for example we have 2 lines of codes Line-1 followed by Line-2. Synchronous means Line-2 can not start running until the Line-1 has finished executing.
(Slide - Stack)
JavaScript is single-threaded, that means only one statement is executed at a time, so it has a single call stack. The call stack is used to store all the execution context created during the code execution. The call stack has a LIFO structure which means that the items can be added or removed from the top of the stack only. And an Execution Context is an abstract concept of an environment where the JavaScript code is evaluated and executed. 
(Slide - Example of synchronous javascript)
So let's see the example:
Step 1: The console.log("Print 1")is pushed into the call stack and executed, once done with execution, it is then popped out of the stack. Now the stack is empty and ready for any next instruction to be executed.
Step 2: console.log("Print 2"); // is the next instruction is pushed and the same thing repeats until - Step 3: is executed and there is nothing left to push and execute.
