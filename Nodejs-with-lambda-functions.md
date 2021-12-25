# NodeJs With Lambda Functions
- [Introduction](#introduction)
- [What is Node.js?](#what-is-node.js?)
- [How Node.js Works?](#how-node.js-works?)
- [Why Node.js?](#Why-node.js?)
- [What is AWS Lambda function ?](#moving-to-hosted-test-and-beyond)
- [How AWS Lambda works?](#How-AWS-Lambda-works?)
- [AWS Lambda concepts](#AWS-Lambda-concepts)
- [Why AWS Lambda?](#Why-AWS-Lambda?)
- [How to use AWS Lambda function](How-to-use-AWS-Lambda-function)

## Introduction
This article is going to discuss how we can run the code on AWS lambda with a simple example and what are core concepts of AWS Lambda

## What Is Node.js?
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
1. Scalability
2. Fast and Reliable
3. Great ecosystem
4. Easy to learn

## What is AWS Lambda function ?
AWS Lambda is an Amazon Web Services serverless computing service, sometimes known as FaaS (Function as a Service). It supports a diverse set of possible triggers, such as incoming HTTP requests, messages from a queue, customer emails, changes to database records, user authentication, messages arriving at web sockets, client device synchronisation, and much more. AWS Lambda also allows you to concentrate on your core product and business logic rather than maintaining the operating system (OS), access control, and so on.

## How AWS Lambda works?
Clients give information to Lambda. Clients might be anyone who sends AWS Lambda queries. This might be an application or one of Amazon's other services.

Lambda takes requests and, according on the size, amount, or volume of the data, executes them on the number of containers specified. Requests are then sent to a container for processing. A container holds the code that the user gave to answer the inquiry.

As the number of requests increases, so does the number of containers produced. When the number of requests decreases, so does the number of containers.

![alt text](http://url/to/img.png)

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
All that remains after generating lambdas is to specify triggers, which are events that can activate Lambda functions. To do so, go to the function console and select the Add Trigger button. Choose a service, such as DynamoDB, and setup it using that lambda function.

### Lambda layers
Lambda layers are a crucial technique for distributing libraries, custom runtimes, and other critical function dependencies. This AWS component also allows you to manage your development function code independently of the unchangeable code and resources that it relies on.

### Throttle
AWS has a Throttle button that disables concurrent execution of Zero, preventing future execution of that function.

When the timeout period expires, AWS Lambda ends the execution of your Lambda function. As a recommended practise, set the timeout value depending on the estimated execution time to avoid your function from lasting longer than planned. For example, if the program terminates after 15 minutes. Additional requests fail with such a throttling error when come across a lot faster than your function can scale or when your function is at maximum concurrency.

### Lambda logs
At Lambda we can check logs easily. Click on Monitoring tab and click on View logs in Cloudwatch.
Where you may keep an eye on logs for performed functions. Logs will be updated if you click the refresh symbol in the upper right corner.

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

1. Step 1: 
Open AWS Console, Choose Lambda from the Services drop-down menu

2. Step 2: 
Select the Create Function option.

3. Step 3: 
Select any of the options from below.
```
1. Author from scratch
2. Use a blueprint
3. Browse serverless app repository
```

4. Step 4: 
Start to writing a function
AWS offers an interactive editor to design and test the lambda function. Following the creation of lambda, you will be sent to the newly constructed lambda console.
```javascript
exports.handler = async (event) => {
    const response = {
      statusCode: 200,
      body: JSON.stringify({msg: `Hello from lambda!`})
    }
    return response;
};
```

5. Step 5: 
Go to the API Gateway and create a new API. On integration dropdon choose Lambda. Amazon now requests some information about how we want to utilise the API. Fill in the blanks and press the "Create" button.

6. Step 6: 
Amazon will now build a new API in API Gateway and associate it with your Lambda function. Now you can open that url

![alt text](http://url/to/img.png)

## Conclusion
Using AWS Lambda, We can build a service without managing servers. We now pay for what We've consumed rather than a set amount each month.