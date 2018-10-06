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
* Messages are 256 KB in size
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

### What is SNS?
* AWS SNS (Simple Notification Service) is a web service that makes it easy to set up, operate, and send notifications from the cloud. It provides developers with highly scalable, flexibile, and cost-effective capability to publish messages from an application and immediately deliver them to subscribers or other applications

* SNS allows you to group multiple recipients using topics. Topic is an "access point" for allowing recipients to dynamically subscribe for identical copies of the same notification. One topic can support deliveries to multiple endpoint types

* To prevent messages from being lost, all messages published to SNS are stored redundantly across multiple AZs

### SNS Benefits
* Instantaneous, push-based delivery (no polling)
* Simple APIs and easy integration with applications
* Flexible message delivery over multiple transport protocols
* Inexpensive, pay-as-you-go model with no up-front costs
* Web-based AWS management console offers the simplicity of a point-and-click interface

### SNS vs SQS
* Both messaging services in AWS
* SNS - Push
* SQS - Polls (Pulls)

### SNS Pricing
* User pay $0.50 per 1 million Amazon SNS Request
* $0.06 per 100,000 notification deliveries over HTTP
* $0.75 per 100 notification deliveries over SMS
* $2.00 per 100,000 notification deliveries over Email

### Elastic Transcoder
* Media transcoder in the cloud
* Convert media files from their original source format in to different formats that will play on smartphones, tablets, PCs, etc
* Provides transcoding presets for popular output formats, which means that you do not need to guess about which settings work best on particular devices
* Pay based on the minutes that you transcode and the resolution at which you transcode

### What is API Gateway?
API Gateway is a fully managed service that makes it easy for developers to publish, maintain, monitor, and secure APIs at any scale.

### What is API Caching?
API caching can reduce the number of calls made to your endpoint and also improve latency of the requests to your API. When you enable caching for a stage, API Gateway caches responses from your endpoint for a specified TTL (time-to-live) period, in seconds. API Gateway then responds to the request by looking up the endpoint response from the cache instead of making a request to your endpoint.

### What can API Gateway do?
* Low cost and efficient
* Scales effortlessly
* You can throttle requests to prevent attacks
* Connect to CloudWatch to log all requests

### Same Origin Policy
In computing, the same-origin policy (web app security model) states that a web browser permits scripts contained in a first web page to access data in a second web page but only if both web pages have the same origin.

### Cross-Origin Resource Sharing (CORS)
* CORS is one way the server at the other end (not the client code in the brower) can relax the same-origin policy
* Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources (e.g. fonts) on a web page to be requested from another domain outside the domain from which the first resource was served
* Error - "Origin policy cannot be read at the remote resource?" - You need to enable CORS on API Gateway

### Exam Tips - API Gateway
* Remember what API Gateway is at a high level
* API Gateway has caching capabilities to increase performance
* API Gateway is low cost and scales automatically
* You can throttle API Gateway to prevent attacks
* You can log results to CloudWatch
* If you are using JavaScript/AJAX that uses multiple domains with API Gateway, ensure that you have enabled CORS on API Gateway

### What is streaming data?
* Streaming data is data that is generated continuously by thousands of data sources, which typically send in the data records simultaneously and in small sizes (KB)
* Streaming data includes:
    * Purchases from online stores
    * Stock prices
    * Game data
    * Social network data
    * Geospatial data
    * IoT sensor data

### What is Kinesis?
Amazon Kinesis is a platform on AWS to send your streaming data to. Kinesis makes it easy to load and analyze streaming data.

### What are the core Kinesis Services?
* Kinesis Streams
* Kinesis Firehose
* Kinesis Analytics

### Kinesis Streams
* Kinesis Streams consist of shards
    * Five transactions per second for reads, up to a maximum total data read rate of two 2 Mbps and up to 1,000 records per second for writes, up to a maximum toala data write rate of 1 Mbps
    * The data capacity of your stream is a function of the number of shards that you specify for the stream. The total capcity of the stream is the sum of the capacities of its shards

### Kinesis Firehose
Amazon Kinesis Data Firehose is the easiest way to reliably load streaming data into data stores and analytics tools. It can capture, transform, and load streaming data into Amazon S3, Amazon Redshift, Amazon Elasticsearch Service, and Splunk, enabling near real-time analytics with existing business intelligence tools and dashboards you’re already using today. It is a fully managed service that automatically scales to match the throughput of your data and requires no ongoing administration. It can also batch, compress, transform, and encrypt the data before loading it, minimizing the amount of storage used at the destination and increasing security.

### Kinesis Analytics
Amazon Kinesis Data Analytics is the easiest way to process streaming data in real time with standard SQL without having to learn new programming languages or processing frameworks. Amazon Kinesis Data Analytics enables you to query streaming data or build entire streaming applications using SQL, so that you can gain actionable insights and respond to your business and customer needs promptly.

### Exam Tips - Kinesis
* Know the difference between Kinesis Streams and Kinesis Firehose
* Understand what Kinesis Analytics is

## Section 9 Quiz

**1. What does Amazon SWF stand for?**
* Simple Work Flow

**2. What does Amazon SES stand for?**
* Simple Email Service

**3. What happens when you create a topic on Amazon SNS?**
* An Amazon Resource Name is created

**4. What is the difference between SNS and SQS?**
* SNS is a push notification service, whereas SQS is a message systemn that requires worker nodes to poll the queue

**5. What application service allows you to decouple your infrastructure using messaged based queues?**
* SQS

**6. What does a "domain" refer to in Amazon SWF?**
* A collection of related workflows

**7. By default, EC2 instances pull SQS messages from an SQS queue on a FIFO (First In First out) basis.**
* False

**8. Amazon's SQS service guarantees a message will be delivered at least once.**
* True

**9. Amazon SWF ensures that a task is assigned only once and is never duplicated.**
* True

**10. Amazon SWF restricts individuals to use specific programming languages.**
* False
