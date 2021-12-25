# NodeJs With Lambda Functions
- [Introduction](#introduction)
- [What is Node.js?](#what-is-node.js?)
- [How Node.js Works?](#how-node.js-works?)
- [Why Node.js?](#Why-node.js?)
  - [Scalability](#developer-rig-usage)
  - [Fast and Reliable](#fast-and-reliable)
  - [Great ecosystem](#Great-ecosystem)
  - [Scalability](#scalability)
  - [Easy to learn](#Easy-to-learn)
- [Where to use Node.js?](#Where-to-use-Node.js?)
- [Moving to Hosted Test (and beyond!)](#moving-to-hosted-test-and-beyond)
  - [Webpack Config](#webpack-config)
  - [Authentication](#authentication)
- [File Structure](#file-structure)
  - [dist](#dist)
  - [public](#public)
  - [src](#src)

## Introduction
Here we going to discuss how we can run the Node.js application on AWS lambda with a simple example

## What is Node.js?
It's a JavaScript runtime environment that allows you to run JS code outside of a browser.

The Back-End Developer will be able to utilise Node js in conjunction with javascript to create a dynamic web page and retrieve data from a database before sending the page to the user's browser.

## How Node.js Works?
Node.js is an event-driven programming language. The server is essentially made up of a single thread that processes events one by one.

Let's take an simple example, There is one ticket counter to book ticket. if you were only one on queue you can get the ticket instantly. But all of sudden,  queue gets bigger if there were only one counter, things went wrong. Consider each new thread as a new ticket-counter employee. The browsers are the people at queue.

Whenever a new request is received, it is given its own thread. As a result, rather than waiting for a blocked IO operation to complete, the server starts processing it and registers a callback function. After that, the server swiftly goes on to the next event.

When the IO action is finished, the server will process the callback as soon as it has time. As a result, the server never has to start new threads or switch between them, resulting in little overhead.

On Node.js event loop is one of the core concept. It's a software that sits and waits for events to happen before dispatching them. Another thing to keep in mind is that JavaScript and Node are both single-threaded.

It is based on the Single Threaded Event Loop Model. The processing approach of Node JS is mostly built on Javascript events with a Javascript callback system.


## Why Node.js?

### Scalability
Node.js can handle a large number of requests at the same time because of it's asynchronus nature. In a simple note, Whenever Node.js get's an request it register a event and get ready for next one. This keeps your RAM from being overworked. 

### Fast and Reliable
Because it is based on Google Chrome's V8 JavaScript engine, Node.js is extremely fast. Its library executes code very quickly. When conducting operations, Node.js employs a non-blocking paradigm. It manages a single asynchronous thread of requests. This minimises both CPU and memory use. Your app will be lighter as a result of this.

### Great ecosystem
You can find 10M free code packages to use with Node.js on the npm (Node.js package management).

### Easy to learn
A developer that is familiar with JavaScript will have a head start with Node.js. Of course, you'll need to understand backend development fundamentals, but knowing the programming language will make things a lot easier.


## Where to use Node.js?
1. Chat applications
2. Video streaming applications
3. For web apps and server-side proxies.

## Building app using express
Express is a lightweight and adaptable Node.js web application framework that offers a comprehensive range of functionality for online and mobile apps.

```javascript
const express = require('express')
const app = express()
const port = 3000

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.listen(port, () => {
  console.log(`Server running on port: ${port}`)
})
```

## What is AWS lambda function ?
AWS Lambda is an Amazon Web Services serverless computing service, sometimes known as FaaS (Function as a Service). It supports a diverse set of possible triggers, such as incoming HTTP requests, messages from a queue, customer emails, changes to database records, user authentication, messages arriving at web sockets, client device synchronisation, and much more. AWS Lambda also allows you to concentrate on your core product and business logic rather than maintaining the operating system (OS), access control, and so on.

## How AWS Lambda works?
Clients give information to Lambda. Clients might be anyone who sends AWS Lambda queries. This might be an application or one of Amazon's other services.

Lambda takes requests and, according on the size, amount, or volume of the data, executes them on the number of containers specified. Requests are then sent to a container for processing. A container holds the code that the user gave to answer the inquiry.

As the number of requests increases, so does the number of containers produced. When the number of requests decreases, so does the number of containers.

## AWS Lambda concepts

### Function
A function is a resource in AWS Lambda that executes your code. Functions contain event-processing code as well as a runtime that routes requests and answers between Lambda and the function. You supply the code, and you may utilise the offered runtimes or write your own.

### Runtime
Lambda runtimes enable the execution of functions written in multiple languages in the same basic execution environment. You arrange your function to utilise the appropriate runtime for your programming language.

### Event
A JSON-formatted document containing data for a function to process is what an event is. The event is converted to an object by the Lambda runtime and sent to your function code. When you call a function, you define the event's structure and contents. When an AWS service calls your function, the event is defined by the service.

### Concurrency
The amount of requests that your function is serving at any given moment is referred to as concurrency. When your function is called, Lambda creates an instance of it to handle the event. When the function code has completed its execution, it is ready to process another request. If the function is called again while a request is being processed, another instance is created, increasing the function's concurrency.

### Trigger
A trigger is a resource or setting that causes a Lambda function to be called. This includes AWS services that may be configured to launch a function, your own apps, and event source mappings.

### Lambda layers
Lambda layers are a crucial technique for distributing libraries, custom runtimes, and other critical function dependencies. This AWS component also allows you to manage your development function code independently of the unchangeable code and resources that it relies on.

## Why AWS Lambda?

### Scalability
When it comes to scalability, Lambda can rapidly scale up to a high number of simultaneous executions, with the number of concurrent executions determined by the number of concurrent executions requested. Scaling down is handled automatically; when the Lambda function execution completes, all resources connected with it are deleted automatically.

### Completely dependent on events
Lambda is entirely event-driven; it will only run when called upon. This is great for application services that have periods of low demand followed by times of high traffic.

### Cost effective
Lambda's following a strategy, which includes a significant free tier, is one of the most enticing for cost reductions. Lambda billing is based on the amount of memory utilised, the number of requests, and the execution time, all of which are rounded up to the closest 100 milliseconds. When compared to EC2's second-based pricing, this is a major step forward for fine-grained billing in order to avoid paying for spare compute resources.

### Don't need to manage
You will not be required to install, maintain, or manage any software.

## How to use AWS Lambda function

1. Step 1
Open AWS Console, Choose Lambda from the Services drop-down menu

2. Step 2
Select the Create Function option.

3. Step 3
Select any of the options from below.
```
1. Author from scratch
2. Use a blueprint
3. Browse serverless app repository
```

4. Step 4
Start to writing a function
AWS offers an interactive editor to design and test the lambda function. Following the creation of lambda, you will be sent to the newly constructed lambda console.
```javascript
exports.handler = (event, context, callback) => {
  console.log("My first lambda function!")
  callback()
}
```

## API Gateway


## Setting triggers
All that remains after generating lambdas is to specify triggers, which are events that can activate Lambda functions. To do so, go to the function console and select the Add Trigger button. Choose a service, such as DynamoDB, and setup it using that lambda function.

## Lambda logs
At Lambda we can check logs easily. Click on Monitoring tab and click on View logs in Cloudwatch.
Where you may keep an eye on logs for performed functions. Logs will be updated if you click the refresh symbol in the upper right corner.

## Throttle
AWS has a Throttle button that disables concurrent execution of Zero, preventing future execution of that function.

When the timeout period expires, AWS Lambda ends the execution of your Lambda function. As a recommended practise, set the timeout value depending on the estimated execution time to avoid your function from lasting longer than planned. For example, if the program terminates after 15 minutes. Additional requests fail with such a throttling error when come across a lot faster than your function can scale or when your function is at maximum concurrency.

## Conclusion
AWS Lambda is a serverless, event-driven computing solution that allows you to run code for almost any form of application with less effort, cost effective and having higher scalability.