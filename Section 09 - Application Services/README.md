# Section 9: Application Services

This section will cover an in-depth overview on AWS Application Services.

### What is SQS?
* Amazon SQS (Simple Queueing Service) is a web service that give you access to a message queue that can be used to store messages while waiting for a computer to process them
* SQS is a distributed queue system that enables web service applications to quickly and reliably queue messafes that one component in the application generates to be consumed by another component. A queue is a temporary repository for messages that are awaiting processing

* Using SQS you can decouple the components of an application so they run independently, easing message management between components
* Any component of a distributed application can store messages in the queue. Messages can contain up to 256 KB of text in any format. Any component can later retrieve the messages programmatically using the SQS API

* The queue acts as a buffer between the component producing and saving data, and the component receiving the data for the processing. This means that the queue resolves issues that arise if the producer is producing work faster than the consumer can process it, or if the producer or consumer are only intermittently connected to the network

### Queue Types
There are two types of queue:
* Standard queues (default)
* FIFO queues (first-in-first-out)

### Standard Queues
A standard queue is the default AWS SQS type. A standard queue lets you have nearly-unlimited number of transaction per second. Standard queues guarantee that a message is delivered at least once. However, occasionally (because of the highly-distributed architecture that allows high throughput) more than one copy of a message might be delivered out of order. Standard queues provide the best-effort ordering which ensures that messages are generally delivered in the same order as they are sent.

### FIFO Queues
The most important features of FIFO queue is the FIFO (first-in-first-out) delivery and exactly-once processing: the order in which messages are sent and received is strictly preserved and a message is delivered once and remains available until a consumer processes and deletes it; duplicates are not introduceds into the queue. FIFO queues also support message groups that allow multiple ordered message groups within a single queue. FIFO queues are limited to 300 TPS (transactions per second) but have all the capabilities of standard queues.

### SQS Key Facts
* SQS is pull-based, not pushed-based
* Messages are 256 KD in size
* Messages can be kept in the queue from one minute to 14 days
* Default retention period is four days
* SQS guarantees that you messages will be processed at least once

### SQS Visibility Timeout
* The visibility timeout is the amount of time that the messages is invisible in the SQS queue after a reader picks up that message
* Default visibility timeout is 30 seconds
* Increase it if your task takes > 30 seconds
* Maximum is 12 hours

### SQS Long Polling
* SQS long polling is a way to retrieve the messages from your SQS queues
* While the regular short polling returns immediately, long polling does not return a response until a message arrives in the message queue, or the long poll times out
* Long polling can save money

### Exam Tips - SQS
* SQS is a distributed messages queueing system
* Allows you to decouple the components of an application so that they are independent
* Pull-based not push-based
* Standard queue (default): best-effort ordering; message delivered at least once
* FIFO queues (first-in-first-out) - ordering strictly preserved, message delivered once, no duplicates, e.g. good for banking transactions which need to happen in strict order
* Visibility timeout
    * Default is 30 seconds - increase if your task takes > 30 seconds to complete
    * Max is 12 hours
* Short polling - returned immediately even if no messages are in the queue
* Long polling - polls the queue periodically and only returns a response when a message is in the queue for the timeout is reached

### SWF
Amazon SWF (Simple Workflow Service) is a web service that makes it easy to coordinate work across distributed application components. SWF enables applications for a range of use cases.

### SWF Workers
Workers are programs that interact with SWF to get tasks, process received tasks, and return the results.

### SWF Decider
The decider is a program that controls the coordination of tasks, i.e. their ordering, concurrency, and scheduling according to the application logic.

### SWF Workers and Deciders
* The workers and the decider can run on cloud infrastructure, such as AWS EC2, or on machines behind firewalls. SWF brokers the interactions between works and the decider. It allows the decider to get consistent views into the progress of tasks and to initiate new tasks in an ongoing manner
* At the same time SWF stores tasks, assigns them to workers when they are ready, and monitors their progress. SWF ensures that a task is assigned only once and is never duplicated. Since AWS maintains the application's state durably, workers and deciders don't have to keep track of execution state. They can run independently and scale quickly

### SWF Domains
* Your workflow and activity types and the workflow execution itself are all scoped to a domain. Domains isolate a set of types, executions, and task lists from others within the same account
* The parameters are specified in JSON format

### How long for workflows?
Maximum workflow can be one year and the value is always measured in seconds

### SWF vs SQS
* SWF presents a task-oriented API, whereas SQS offers a message-oriented API
* SWF ensures that a task is assigned only once and is never duplicated, with SQS you need to handle duplicated messages and may also need to ensure that a message is processed only once
* SWF keeps track of all the task and events in an application with SQS you need to implement you own application-level tracking, especially if your application uses multiple queues
