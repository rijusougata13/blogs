---
title: "How Javascript works in your browser 🤨?"
datePublished: Tue Aug 15 2023 20:56:20 GMT+0000 (Coordinated Universal Time)
cuid: cllcsacbe000209l8hwvhgcwu
slug: how-javascript-works-in-your-browser
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692131876676/ddc7ce51-88bb-4299-a584-6463243b796a.jpeg
tags: javascript, development, workflow, web-development

---

You folks have been writing javascript code for a long but have you wondered how javascript works? What happens when you write a small program, and how does that get executed?

**<mark>Javascript is a single-threaded language but works as an asynchronous. Wait! what do you mean by single-threaded and asynchronous? A single thread means there is only one thread and one task can be executed at a time. So how javascript can be asynchronous?</mark>**

It might sound strange to you, but in this blog, we will understand how javascript works in-depth and you can understand why I said the above statement.  
So before starting let's do a quick exercise.

```javascript
console.log("a");

setTimeout(()=>{
    console.log("b");
},0)

var promise= new Promise(function(resolve, reject){
    resolve();
});

promise.then((resolve)=>{
    console.log("c");
});
console.log("d");
```

So you have one minute in your hand, what will be the output?

⏰ ⏰ ⏰....

Times up!! If you have guessed

```javascript
a
b
c
d
```

or

```javascript
a
d
b
c
```

If you guessed any of these solutions, you should follow along till the end and check what you have missed or else you can still stay to freshen up your memory 😄.

### `Javascript Engine`

Javascript Engine is the one that helps to execute javascript code. When you pass a javascript code, it executes them line by line and converts them to machine-understandable language.

Popular javascript engines are v8, chakra, and spider-monkey. These are all javascript engines which mainly consist of a call stack and memory heap.

**Call stack:** This is where all the tasks get executed one by one.

**Memory heap:** This is where your code's memory allocation occurs.

![collected](https://felixgerschau.com/static/b452488bd7eeac0405c48f164da6280d/5a190/stack-heap-pointers.png align="center")

Yes, that's it. Now you know how everything works right?

.

.

.

Wait 😅, I am joking, JavaScript is not that simple. There are lots of things other than the javascript engine. Let's discuss them one by one.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692125904690/0f2994d0-a731-4dc5-a389-d4373d9231de.png align="center")

This is the whole structure which runs behind to make javascript code work.

### Call Stack

The call stack is a simple stack-like structure which works as LIFO (Last In First Out). You all know what stack is so nothing much to discuss about its properties. Its main task is whatever is inside this stack just execute them one by one. When javascript starts executing scripts it first creates a **Global Execution Context** and pushes it in the call stack. Its acts as a global variable. Then it just pushes another task one by one until there is nothing left. Let's see a demo.

```javascript
const B=()=>{
console.log("hello");
}
const A=()=>{
  B();
}
A();
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692126828228/f0699a2b-b5ca-47b9-99ce-a42cb202eee8.png align="center")

As you can see at the very first Global Execution context is inserted. Then the function A is called. It remain there and called B. Then after B, console.log got executed and popped from the stack. Then B, then A and at the very end GE got out from the call stack.

Now you may be thinking if it happens like this what happens when there is something async operation? Won't it block the stack and the browser should stop executing others until that async operation gets executed?

Yes! good catch. It should be blocked and the browser shouldn't be able to perform any other task till the async operation finishes. <mark>But javascript doesn't execute async operation in this call stack directly. Its moves the async operation to a different place (web api environment), wait for it to finish there and then after going through some process it comes to the call stack and gets executed.</mark>

### Memory Heap

This is where memory allocation happens of the variable which is defined in your code.

### Web APIS

Web APIs are a set of functions provided by the browser that the JavaScript engine can utilize. This consists of setTimeOut, setInterval, async-await, promises and many more. Javascript executes every task one by one. But when it encounters any async operation it doesn't push it in the call stack rather it lets it execute in the web APIs environment. It helps to prevent blocking other tasks and execute them asynchronously with the normal task.

### CallBack Queue

As we have talked async operations are get executed in a separate environment. Now what happens next when the waiting time gets over? It doesn't know what to do now. Now callback queue handles everything after this. It's a normal queue-type data structure, which works as FIFO (First In First Out). Assume there are two async operations.

```javascript
setTimeOut(()=>{
console.log("a");
},100);

setTimeOut(()=>{
console.log("b");
},200);
```

Both of them are thrown to separate environments during execution. But after 100ms console.log("a") gets out and it goes to the callback queue and waits for its turn. Then after another 100ms (total 200ms) console.log("b") comes out and is pushed into the callback queue.

This callback queue doesn't execute them. Only the call stack has the power, the callback queue's only task is to track the order of async operations and hold them until and unless the call stack gets empty.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692128891285/8c18f664-d978-40eb-8cf5-9a59ac8c8b5f.png align="center")

### Job Queue

Job queue also known as micro-task queue. It's also the same as a callback queue. The only difference is it has higher priority than the callback queue. It's used by promises. So if a promise and setTimeout has the same wait time, promises will be given higher priority as it gets inserted in the job queue and other async task gets inserted in the callback queue.

### Event Loop

At the very end event loop comes into the picture. Its runs always and check if the call stack is empty or not. If it's empty it takes a task from the callback queue and job queue and sends it to the call stack. It gives higher priority to the jobqueue than the callback queue.

Javascript is a vast topic, but I hope I am able to clear a little bit of how javascript works. So let's recap once.

<mark>sync task -&gt; call stack -&gt; get executed -&gt; pop from call stack</mark>

<mark>async task -&gt; wait and being executed in web apis environment -&gt; go to callback queue -&gt; event loop move the task to call stack -&gt; get executed -&gt; pop from call stack</mark>

This is in short whatever we have learned till now.

Now let's get back to the very first question I asked you, folks.  
Adding the question again for you.

```bash
console.log("a");

setTimeout(()=>{
    console.log("b");
},0)

var promise= new Promise(function(resolve, reject){
    resolve();
});

promise.then((resolve)=>{
    console.log("c");
});
console.log("d");
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692131286565/9fec4824-b3e5-456c-84e4-15dd6af31729.png align="center")

From the above diagram, you can understand that at very first console.log('a') gets inserted into the call stack and gets executed and pops out. Then setTimeOut goes to web APIs as well as the promise. Then console.log('d') gets into the call stack and gets executed and pops out.  
Then both setTimeout and promise's time get over and they came out. setTimeOut goes into the call back queue and promise goes into the job queue.  
Now event loop check call stack is empty and gives priority to the job queue. So, console.log('c') gets inserted in the call stack and gets executed.  
At the very end console.log('b') gets inserted into the call stack and gets executed.

so the output looks like this

```bash
a
d
c
b
```

I hope now it's all clear how everything works and why the output looks like this. If you can correlate everything here, you have achieved something new today 😄.

So let it end here. We will discuss more about the javascript operation in another blog.  
If you enjoyed this article you can support me by [**buying me a coffee**](https://www.buymeacoffee.com/rijusougata13) and following me on [**twitter**](https://twitter.com/rijusougata13).