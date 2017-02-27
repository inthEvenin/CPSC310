# Async

### Intro

- To take the advantage of increasing number of cores, most modern programming language support some model concurrent execution.
- In JavaScript, we can only execute in one thread; a thread does exist in both Node and the browser to ensure that long running tasks can be offloaded in a way that does not block the main thread (*asynchronous execution*).
- In JavaScript, functions execute on the call stack, and they always execute to completion (one method can execute at a time and another cannot run until the first one finishes).
- Functions in JavaScript should not take *too long*. Commonly-held measure in JavaScript is **16ms**; exceeding this value will cause the UI to miss a refresh on a **60hz** monitor.
- Stuttering caused by computations exceeding these threshholds are referred to as ***jank*** within the browser.
- In practice, many operations take more than 16ms to happen
  - Network latency can range into hundreds of milliseconds
  - Reading or writing from disk can easily take more than a second for larger files. 
  - JavaScript has a thread pool that has limited capabilities but is ideal for handling blocking operations.
  - Rather than executing on the main thread, these execute in a separate thread pool and are returned to the call stack via **callbacks** when the event loop is idle.

### Callback shortcomings

- There are **two** common problems manifest with callbacks in practice.
  - Handling error is difficult because callbacks are invoked but they do not ***return*** a value. This means any information about executions of the function making the callback must take place in the parameters.
  - The problem becomes harder to manage when the callbacks depend on the output of previous callback functions. 
    - This pattern arrises from our natural desire to want the **apparent execution** to proceed from **top-to-bottom** in the source code file.
    - One significant problem with callback-based error handling is that exceptions **cannot be effectively caught**. Since the callback is not being executed in the context of its originating function, there is **no** '*parent*' method for the catch to exist in.
    - Nested callbacks are often referred as *callback hell*.

### Promises

- **Promises** are mechanism to address two of the largest shortcoming of callback hell, namely:
  - Flattening callback chains
  - Enabling try/catch for error handling.
- Although promises do enable try/catch to work properly, they **do not** provide any functionality that would not be possible with callbacks alone.
- Their main benefit is that they are **easier** for developers to **read** and **understand** making it more likely that developers will **'do the right thing'** in these **often-complex program sequences**.
- Promises can only have three states:
  - **Pending** before it is done its task.
  - **Fulfilled** if the task has completed successfully.
  - **Rejected** if the task has completed erroneously.
- Promises can only transition to **fulfilled** or **rejected** once and cannot change between **fulfilled** and **rejected**; this process is called **settling**.
- Promises are **objects** with two methods **then** and **catch**.
  - **then** is called when the promise is settled successfully.
  - **catch** is called when the promise is settled with an error.
  - There can be multiple **catch** statements (for example, in a 5 step flow, you could catch after the first two, fix the problem, and then continue the flow while still having a final catch at the end).
- One nice feature of Promises is that they are able to be **composed**; this is helpful when you are trying to manage multiple concurrent promise executions in parallel (**Promise.all**).
- **Promise.race** allows for starting multiple async calls; then is called when the **first** promise **fulfills**, rather then when **all** of them **fulfill** as is required for **Promise.all**.
  - This can be handy when there are multiple ways to accomplish a task but cannot know which will be fastest in advance
  - Or if you want to show progress on a task by updating the user when data starts to become available rather than waiting for a full operation to be complete.
- It is *strongly encouraged* that you end every **then** sequence with a **catch** even if you do not do any meaningful error handling.
  - This is because promises settle asynchronously and will fail silently if rejections are not caught; they will not escape to a global error handler. 
  - Another mistake to watch when working with Promises is when **then** is not applied to the right object.