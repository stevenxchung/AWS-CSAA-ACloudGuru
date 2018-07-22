# Section 2: AWS - 10,000 Feet Overview

This section will cover a top-level overview on the AWS services tested in the Solutions Architect exam

* AWS officially launched in 2006
* By the numbers, AWS services have grown from 82 in 2011 to over 1300+ in 2017

### Terminology
* What is a Region? A Region is a physical location in the world which consists of two or more AZ's
* What is an AZ? An AZ (Availability Zone) is simply a data center
* What is an Edge Location? Edge Locations are endpoints for AWS which are used for caching content. Typically this consists of CloudFront, Amazon's CDN (Content Delivery Network)

### Compute Service
* EC2 (Elastic Compute Cloud) - Virtual machines inside the AWS platform
* EC2 container service - Run and manage Docker containers at scale
* Elastic Beanstalk - For developers who do not understand AWS who just want to upload their code
* Lambda - A code uploaded to the cloud where you can control when it executes (no need to worry about physical or virtual machine)
* Lightsail - Amazon's VPN (virtual private network) service essentially a watered-down version of EC2
* Batch - Used for batch computing in the cloud

### Storage Service
* S3 (Simple Storage Service) - An object based- storage where we can upload files into buckets in the cloud
* EFS (Elastic File System) - A network-attached service
* Glacier - Data archival service
* Snowball - Way to bring in large amounts of data into the AWS data center
* Storage Gateway - Virtual Machines which will replicate information back to S3

### Database Services
* RDS (Relational Database Service) - Service which works with MySQL, PostgreSQL, Oracle
* DynamoDB - For non-relational databases
* ElastiCache - A way of caching commonly queried items from a database
* Red Shift - Built for data warehousing

### Migration Services
* AWS Migration Hub - Tracking service which allows application tracking during migration
* Application Discovery Service - Automated set of tools which not only detects what applications we have but also tracks the dependencies for our application
* Database Migration Service - A way to visualize migrations in action
* Server Migration Service - Helps migrate physical and virtual servers to the cloud
* Snowball - Also a migration tool as well as a storage service

### Networking & Content Delivery
* VPC (Virtual Private Cloud) - Essentially a virtual data center where we can configure things such as firewalls, AZ's, etc.
* CloudFront - Stores information closer to the users
* Route53 - Amazon's DNS service
* API Gateway - Is a way of creating our own APIs for our services to talk to
* Direct Connect - A way of running a dedicated line from a data center into Amazon which will directly connect into a VPC

### Developer Tools
* CodeStar - Project management service
* CodeCommit - Source control service or place to store code
* CodeBuild - Once service is ready, this service will compile, run tests, and produce software packages which will enable deployment
* CodeDeploy - Service which automates deployments to EC2 instances, on premise instances, and lambda functions for example
* CodePipeline - Continuous delivery pipeline which will automate the steps required to release software
* X-Ray - Debug service which will help find root causes and performance bottlenecks
* Cloud9 - IDE environment which will allow development on the cloud

### Management Tools
* CloudWatch - Monitoring service
* CloudFormation - Way of scripting infrastructure
* CloudTrail - Used to log changes to the AWS environment (turned on by default and stores logs for a week)
* Config - Monitors the entire AWS environment
* OpsWorks - Similar to Elastic Beanstalk but more robust and is good tool to automate environments
* Service Catalog - A way of managing catalogs of IT services which are approved to use on AWS
* Systems Manager - A resource manager, typically used for EC2
* Trusted Advisor - Will give advice across multiple disciplines
* Managed Services - A manage service for things such as EC2 instances and auto scaling

### Media Services
* Elastic Transcoder - Resizes videos to be compatible on multiple platforms
* MediaConvert - File-based video transcoding service with broadcast grade features
* MediaLive - Broadcast grade video processing service
* MediaPackage - Prepares and protects videos for delivery over the internet
* MediaStore - Storage service optimized for media
* MediaTailor - Allows the ability to do ads on broadcast grade media

### Machine Learning
* SageMaker - Makes it easy to use deep learning
* Comprehend - Sentiment analysis around data
* DeepLens - Artificially aware camera
* Lex - A way of communicating with customers
* Machine Learning - Service to build machine learning projects
* Polly - Takes text and turns it into speech
* Rekognition - Recognizes objects of interest in images and videos
* Amazon Translate - Translation service
* Amazon Transcribe - Transcribe service

### Analytics
* Athena - Allows SQL queries or files in S3 bucket
* EMR (Elastic Map Reduce) - Used for processing large amounts of data
* CloudSearch - Search service for AWS
* ElasticSearch Service - Search service for AWS
* Kinesis - A way of ingesting large amounts of data into AWS
* Kinesis Video Streams - Allows ingesting of large amounts of data from video streams
* QuickSight - Amazon's business intelligence tool
* Data Pipeline - A way of moving data between different AWS services
* Glue - Used for ETL (Extract Transform and Load)

### Security & Identity & Compliance
* IAM (Identity Access Management) - Amazon's IAM service
* Cognito - Device authentication service
* GuardDuty - Monitors for malicious activity on the AWS account
* Inspector - An agent installed on services such as EC2 to check vulnerabilities
* Macie - Scan S3 buckets for PII (Personal Identity Info)
* Certificate Manager - Way of managing SSL certificates
* CloudHSM - Service which offers dedicated bits of hardware used to store keys
* Directory Service - Way of integrating Microsoft active directory services with AWS services
* WAF (Web Application Firewall) - A layer 7 firewall which stops cross-site scripting or SQL injections
* Shield - Service which helps mitigate DDoS attacks
* Artifact - Portal service which allows downloads of compliance reports

### Mobile Services
* Mobile Hub - Management console for mobile apps
* Pinpoint - Uses targeted push notifications to drive mobile engagement
* AWS AppSync - Updates data in web and mobile applications in real-time
* Device Farm - A way of testing apps on real-life devices
* Mobile Analytics - Analytics service for mobile

### AR/VR
* Sumerian - Used for AR, VR and 3D application design, allows you to use a common set of tools to create environments

### Application Integration
* Step Functions - A way of managing different Lambda functions
* Amazon MQ - A way of queuing messages
* SNS (Simple Notification Service) - Notification service if an account goes over some limit
* SQS (Simple Queue Service) - Queue service which is used for decoupling infrastructure
* SWF (Simple Workflow Service) - Workflow service which creates a workflow map for some processes

### Customer Engagement
* Connect - Essentially is a call center in the cloud
* Simple Email Service - Very scalable service which helps send emails to customers

### Business Productivity
* Alexa For Business - Can use for a variety of business services and tasks
* Chime - Video conferencing similar to Google hangout
* WorkDocs - A drop box for AWS
* WorkMail - Similar to Office 365

### Desktop & App Streaming
* Workspaces - A VDI (virtual desktop infrastructure) solution (running an operating system on AWS cloud)
* AppStream 2.0 - A way to actually stream applications to your desktop

### Internet of Things
* iOT - A way of having thousands or millions of devices sending back data i.e. sensor data such as temperature or humidity to a controller
* iOT Device Management - Used for managing a ton of devices through the AWS service
* Amazon FreeRTOS - Operating system service for microcontrollers
* Greengrass - Software that lets your run local compute, messaging, data caching, sync, and ML inference capabilities for connected devices in a secure way

### Game Development
* GameLift - Service to help develop games in the AWS cloud
