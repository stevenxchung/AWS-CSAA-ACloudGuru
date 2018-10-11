# Section 12: Additional Exam Tips

This section will cover additional exam tips from previous sections.

### What is Kinesis?
* Amazon Kinesis is a fully managed service for real-time processing of streaming data at massive scale. You can configure hundreds of thousands of data producers to continuously put data into an Amazon Kinesis stream

* Think Kinesis when:
    * Consuming big data
    * Stream large amounts of social media, news feeds logs, etc. into the cloud

* Process large amounts of data:
    * Redshift for business intelligence
    * Elastic map reduce for big data processing

### EC2 - EBS Backed vs Instance Store
* EBS backed volumes are persistent
* Instance Store backed volumes are not persistent (ephemeral)
* EBS volumes can be detached and reattached to other EC2 instances

* Instance store volume cannot be detached and reattached to other instances - they exist only for the life of that instance
* EBS volumes can be stopped; data will persist

* Instance store volumes cannot be stopped - if you do this the data will be wiped
* EBS backed = store data long-term
* Instance store = should not be used for long-term data storage

### OpsWorks
* Orchestration Services that uses Chef
* Chef consists of recipes to maintain a consistent state
* Look for the term "chef" or "recipes" or "cook books" and think OpsWorks

### Elastic Transcoder
* Media transcoder in the cloud
* Convert media files from their original source format into different formats that will play on smartphones, tablets, PC's, etc
* Provides transcoding presets for popular output formats, which means that you do not need to guess about which setting work best on particular devices
* Pay based on the minutes that you transcode and the resolution at which you transcode

### SWF Actors
* Workflow Starters - An application that can initiate a workflow
* Deciders - Control the flow of activity tasks in a workflow execution
* Activity Workers - Carry out the activity tasks

### EC2 - Get Public IP Address
* Need to query the instances metadata:
    * curl http://169.254.169.254/latest/meta-data/
    * wget http://169.254.169.254/latest/meta-data/
    * Key thing to remember is that it is an instances **metadata** no user data

### What is AWS Organizations?
* AWS Organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage
* Available in two feature sets:
    * Consolidated billing
    * All features

### Advantages of Consolidated Billing
* One bill per AWS account
* Very easy to track charges and allocate costs
* Volume pricing discount

### AWS Ogranizations and Consolidated Billing - Best Practices
* Always enable multi-factor authentication on root account
* Always use a strong and complex password on root account
* Pay account should be used for billing purposes only. Do not deploy resources in to paying account

### AWS Ogranizations and Consolidated Billing - Notes
* Linked accounts
    * 20 linked accounts only
* Billing alerts
    * When monitoring is enabled on the paying account the billing data for all linked accounts is included
    * You can still create billing alerts per individual account
* CloudTrail
    * Per AWS account and is enabled per region
    * Can consolidate logs using an S3 bucket:
        1. Turn on CloudTrail in the paying account
        2. Create a bucket policy that allows cross account access
        3. Turn on CloudTrail in the other accounts and use the bucket in the paying account

### AWS Ogranizations and Consolidated Billing - Exam Tips
* Consolidated billing allows you to get volume discounts on all your accounts
* Unused reserved instances for EC2 are applied across the group
* CloudTrail is on a per account and per region basis but can be aggregated into a single bucket in the paying account
* AWS Organizations allows you to:
    * Centrally manage policies across multiple AWS accounts
    * Control access to AWS services
    * Automate AWS account creation and management
    * Consolidate billing across multiple AWS accounts

### What is Cross Account Access?
Cross account access makes it easier for you to work productively within a multi-account AWS environment by making it easy for you to switch roles within the AWS Management Console. You can now sign into the console using your IAM user name then switch the console to manage another account without having to enter another username and password.

### What are Tags?
* Key value pairs attached to AWS resources
* Metadata (data about data)
* Tags can sometiems be inherited
    * Autoscaling, CloudFormation, and Elastic Beanstalk can create other resources

### What are resource groups?
* Resource groups make it easy to group your resources using the tags that are assigned to them
* Resource groups contain information such as:
    * Region
    * Name
    * Health checks
* Specific information
    * For EC2 - Public and private IP addresses
    * For ELB - Port configurations
    * For RDS - Database eengine etc

### AWS Resource Groups
There are two types of AWS resource groups:
* Classic resource groups
* AWS systems manager

### What is VPC Peering?
* VPC Peering is simply a connection between two VPCs that enables you to route traffic between them using private IP addresses. Instances in either VPC can communicate with each other as if they are within the same network. You can create a VPC peering connection between your own VPCs, or with a VPC in another AWS account within a **single region**
* AWS uses the existing infrastructure of a VPC to create a VPC peering connection; it is neither a gateway nor a VPN connection, and does not rely on a separate piece of physical hardware. There is no single point of failure for communication or a bandwidth bottleneck

### VPC Peering Limitations
* VPC peering does not support transitive peering relationships
* You cannot create a VPC peering connection between VPCs in different regions
* You cannot create a VPC peering connection between VPCs that have matching or overlapping CIDR blocks

### Direct Connect
AWS Direct Connect makes it easy to establish a dedicated network connection from your premises to AWS. Using AWS Direct Connect, you can establish private connectivity between AWS and your data center, office, or co-location environment, which in many cases can reduce your network costs, increase bandwidth throughput, and provide a more consistent network experience than internet-based connections.

### Direct Connect Benefits
* Increase bandwidth
* Increate reliability
* Reduce costs when using large volumes of traffic

### How is Direct Connect different from a VPN?
* VPN connections can be configured in minuites and are a good solution if you have an immediate need, have low to modest bandwidth requirements, and can tolerate the inherent variability in internet-based connectivity
* AWS Direct Connect does not involve the internet; instead, it uses dedicated, private network connections between your intranet and Amazon VPC

### Direct Connect Connections
* Connections are available in:
    * 1 Gbps
    * 10 Gbps
* Sub 1 Gbps can be purchased through AWS direct connect partners
* Uses ethernet VLAN trunking (802.1Q)

### Security Token Service (STS)
* Grants users limited and temporary access to AWS resources. Users can come from three sources:
    * Federation (typically Active Directory)
        * Uses SAML (Security Assertion Markup Language)
        * Single sing on allows users to log into AWS console without assigning IAM credentials
        * Grants temporary access based off the users Active Directory credentials. Does not need to be a user in IAM
    * Federation with Mobile Apps
        * Use Facebook/Amazon/Google or other OpenID providers to log in
    * Cross Account Access
        * Lets users from one AWS account access resources in another

### Understanding Key Terms
* Federation
    * Combining or joining a list of users in one domain (such as IAM) with a list of users in another domain (such as Active Directory, Facebook, etc)
* Identity Broker
    * A service that allows you to take an identity from point A and join it (federate it) to point B
* Identity Store
    * Services like Active Directory, Facebook, Google, etc
* Identities
    * A user of a service like Facebook, etc

### STS - Exam Tips
* Develop an Identity Broker to communicate with LDAP and AWS STS
* Identity Broker always authenticates with LDAP first, **then** with AWS STS
* Application then gets temporary access to AWS resources

### Active Directory Integration
* Can you authenticate with Active Directory?
    * Yes, using SAML
* Which is done first, SAML to authenticate against Active Directory or Active Directory then SAML credentials?
    * We always authenicate with Active Directory first then receive the SAML

### What is a Workspace?
* A Workspace is a cloud-based replacement for a traditional desktop.
* Quick facts:
    * Workspaces are persistent
    * All data on the D:\ is backed up every 12 hours
    * You do not need an AWS account to login to workspaces
    * Windows 7 experience provided by Windows Server 2008 R2
    * By default, you will be given local admin access so you can install your own apps
    * By default, users can personalize their workspaces but can be locked down by an admin

### What is Docker?
* Docker is a software platform that allows you to build, test, and deploy applications quickly
* Docker is highly reliable: you can quickly deploy and scale applications into any environment and know your code will run
* Docker is infinitely scalable: running Docker on AWS is a great way to run distributed applications at any scale
* Docker packages software into standardized units called Containers:
    * Containers allow you to easily package an application's code, configurations, and dependencies into easy to use building blocks that deliver environmental consistency, operational efficiency, developer productivity, and version control

### Virtualization vs Containerization
* Traditional virtualization has density compromises
* Docker achieves higher density, improved portability by removing the per container Guest OS

### Containization Benefits
* Escape from dependency hell
* Consistent progression from Dev -> Test -> QA -> Prod
* Isolation - performance or stability issues with App A in container A, will not impact App B in container B
* Much better resource managemnet
* Extreme code portability
* Mircoservices

### Docker Components
* Docker image
* Docker container
* Layers/Union file system
* Dockerfile
* Docker Daemon/Engine
* Docker client
* Docker registries/Docker hub

### About ECS
* AWS ECS (EC2 Container Service) is a highly scalable, fast, container management service that makes it easy to run, stop, and manage Docker containers on a cluster of EC2 instances. ECS lets you launch and stop container-based applications with simple API calls, allows you to get the state of your cluster from a centralized service, and gives you access to many familiar EC2 features

* ECS is a regional service that you can use in one or more AZs across a new, or existing VPC to schedule the placement of containers across your cluster based on your resource needs, isolation policies, and availability requirements
* AWS ECS eliminates the need for you to operate your own cluster management and configuration management systems, or to worry about scaling your management infrastructure
* ECS can also be used to create a consistent deployment and build experience, manage and scale batch and ETL workloads, and build sophisticated application architectures on a microservices model

### About Containers
* Containers are a method of operating system virtualization that allows you to run an application and its dependencies in resource-isolated processes
* Containers have everything the software needs to run - including libraries, system tools, code and runtime
* Containers are created from a read-only template called an image

### What's a Docker Image?
* An image is a read-only template with instructions for creating a Docker container. It contains:
    * An ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime
* An image is create from a Dockerfile, a plain text file that specifies the components that are to be included in the container
* Images are stored in a registry, such as DockerHub or AWS ECR

### Container Registries
AWS ECR (EC2 Container Registry) is a managed AWS Docker registry service that is sercure, scalable, and reliable. ECR supports private Docker respositories with resource-based permissions using AWS IAM so that specific users or EC2 instances and access repositories and images. Developers can use the Docker CLI to push, pull, and manage images.

### ECS Task Definitions
* A Task Definition is required to run Docker containers in ECS
* Task Definitions are text files in JSON format that describe one or more containers that form your application
* Some of the parameters you can specify in a task defintion include:
    * Which Docker images to use with the containers in your task
    * How much CPU and memory to use with each container
    * Whether containers are linked together in a task
    * The Docker networking mode to use for the containers in your task
    * What ports from the container are mapped to the host container instance
    * Whether the task should continue to run if the container finishes or fails
    * The command the container should run when it is started
    * What environment variables should be passed to the container when it starts
    * Any data volumes that should be used with the containers in the task
    * What IAM role your tasks should use for permissions

### ECS Services
* An ECS service allows you to run and maintain a specified number (desired count) of instances of a task definition simultaneously in an ECS cluster
* Think of services like auto scaling groups for ECS

### ECS Clusters
* An ECS cluster is a logical grouping of container instances that you can place tasks on. When your first use the ECS service, a default cluster is created for you, but you can create multiple clusters in an account to keep your resources separate
* Concepts:
    * Clusters can contain multiple different container instance types
    * Clusters are region-specific
    * Container instances can only be part of one cluster at a time
    * You can create IAM policies for you clusters to allow or restrict users' access to specific clusters

### ECS Scheduling
* Service Scheduler:
    * Ensures that the specified number of tasks are constantly running and reschedules tasks when a tasks fails
    * Can ensure tasks are registered against an ELB
* Custom Scheduler
    * You can create your own schedulers that meet your business needs
    * Leverage third-party schedulers, such as Blox
* The ECS schedulers leverage the same cluster state information provided by the ECS API to make appropriate placement decisions

### ECS Container Agent
* The ECS container agent allows container instances to connect to your cluster. ECS container agent is included in the ECS optimized AMI but you can also install it on any EC2 instance that supports the ECS specification. The ECS container agent is only supported on EC2 instances
* Pre-installed on special ECS AMIs
* Linux-based:
    * Works with Amazon Linux, Ubuntu, Red Hat, CentOS, etc
    * Will **not** work with Windows

### ECS Security
* IAM Roles:
    * EC2 instances use an IAM role to access ECS
    * ECS tasks use an IAM role to access services and resources
* Security groups attach at the instance-level (i.e. the host and not the task or container)
* You can access and configure the OS of the EC2 instances in your ECS cluster

### ECS Limits
* Soft limits:
    * Default clusters per region = 1000
    * Default instances per region = 1000
    * Default services per region = 500
* Hard limits
    * One load balancer per service
    * 1000 task per service
    * Max 10 containers per task definition
    * Max 10 tasks per instance (host)

### ECS - Exam Tips
* ECS - Amazon's managed EC2 container service which allows you to manage Docker containers on a cluster of EC2 instances
* Containers are a method of operating system virtualization that allows you to run an app and its dependencies in resource-isolated processes
* Containers are created from a read-only template called an Image
* An Image is a read-only template with instructions for creating a Docker container
* Images are stored in a Registry, such as DockerHub or AWS ECR
* ECR is a managed AWS Docker registry service

### ECS - Exam Tips Continued...
* A Task Definition is required to run Docker containers in ECS
* Task Definitions are text files in JSON format that describe one or more containers that form your app
* Think of a Task Definition as a cloud formation template but for Docker
* ECS service allows you to run and maintain a specified number of instances of a task defintion simultaneously in an ECS cluster
* Think of services like auto scaling groups for ECS
* ECS clusters are a logical grouping of container instances that you can place tasks on

### ECS - Exam Tips Continued...
* Clusters can contain multiple different container instance types
* Clusters are region-specific
* Container instances can only be part of one cluster at a time
* You can create IAM policies for you clusters to allow or restrict users' access to specific clusters
* You can schedule ECS in two ways
    * Service scheduler
    * Customer scheduler
* Use ECS agent to connect to ECS instances to your ECS cluster (**Linux only**)
* IAM with ECS to restrict access
* Security groups operate at the instance level not at the task or container level

## Section 12 Quiz
**1. You are a solutions architect working for a company that specialises in ingesting large data feeds (using Kinesis) and then analysing these feeds using Elastic Map Reduce (EMR). The results are then stored on a custom MySQL database which is hosted on an EC2 instance which has 3 volumes, the root/boot volume, and then 2 additional volumes which are striped into a RAID-0 set. Your company recently had an outage and lost some key data and have since decided that they will need to run nightly back ups. Your application is only used during office hours, so you can afford to have some down time in the middle of the night if required. You decide to take a snapshot of all three volumes every 24 hours. In what manner should you do this?**
* Stop the EC2 instance and take a snapshot of each EC2 instance independently. Once the snapshots are complete, start the EC2 instance and ensure that all relevant volumes are remounted

**2. What are the valid methodologies for encrypting data on S3?**
* Server Side Encryption (SSE)-S3, SSE-C, SSE-KMS, or a client library such as S3 Encryption Client

**3. In Identity and Access Management, when you first create a new user, certain security credentials are automatically generated. Which of the below are valid security credentials?**
* Access Key ID, Secret Access Key

**4. Amazon Web Services offer 3 different levels of support, which of the below are valid support levels?**
* Enterprise, Business, Developer

**5. You are a solutions architect working for a large digital media company. Your company is migrating their production estate to AWS and you are in the process of setting up access to the AWS console using Identity Access Management (IAM). You have created 5 users for your system administrators. What further steps do you need to take to enable your system administrators to get access to the AWS console?**
* Generate a password for each user created and give these passwords to your system administrators

**6. Amazon S3 buckets in all Regions provide which of the following?**
* Read-after-write consistency for PUTS of new objects AND Eventually consistent for overwrite PUTS & DELETES

**7. What function of an AWS VPC is stateless?**
* Network Access Control Lists

**8. Which of the following services allows you root access (ie you can login using SSH)?**
* Elastic Map Reduce

**9. When trying to grant an amazon account access to S3 using access control lists what method of identification should you use to identify that account with?**
* The email address of the account or the canonical user ID

**10. You are a solutions architect working for a large oil and gas company. Your company runs their production environment on AWS and has a custom VPC. The VPC contains 3 subnets, 1 of which is public and the other 2 are private. Inside the public subnet is a fleet of EC2 instances which are the result of an autoscaling group. All EC2 instances are in the same security group. Your company has created a new custom application which connects to mobile devices using a custom port. This application has been rolled out to production and you need to open this port globally to the internet. What steps should you take to do this, and how quickly will the change occur?**
* Open the port on the existing security group. Your EC2 instances will be able to communicate over this port immediately

**11. Which of the following is not supported by AWS Import/Export?**
* Export to Amazon Glacier

**12. Which of the following is not a service of the security category of the AWS trusted advisor service?**
* Vulnerability scans on existing VPCs

**13. You work for a market analysis firm who are designing a new environment. They will ingest large amounts of market data via Kinesis and then analyse this data using Elastic Map Reduce. The data is then imported in to a high performance NoSQL Cassandra database which will run on EC2 and then be accessed by traders from around the world. The database volume itself will sit on 2 EBS volumes that will be grouped into a RAID 0 volume. They are expecting very high demand during peak times, with an IOPS performance level of approximately 15,000. Which EBS volume should you recommend?**
* Provisioned IOPS (PIOPS)

**14. What are the different types of virtualization available on EC2?**
* Para-Virtual (PV) & Hardware Virtual Machine (HVM)

**15. Which of the following is not a valid configuration type for AWS Storage gateway?**
* Gateway-accessed volumes

**16. You have started a new role as a solutions architect for an architectural firm that designs large sky scrapers in the Middle East. Your company hosts large volumes of data and has about 250Tb of data on internal servers. They have decided to store this data on S3 due to the redundancy offered by it. The company currently has a telecoms line of 2Mbps connecting their head office to the internet. What method should they use to import this data on to S3 in the fastest manner possible?**
* AWS Import/Export

**17. You are designing a site for a new start up which generates cartoon images for people automatically. Customers will log on to the site, upload an image which is stored in S3. The application then passes a job to AWS SQS and a fleet of EC2 instances poll the queue to receive new processing jobs. These EC2 instances will then turn the picture in to a cartoon and will then need to store the processed job somewhere. Users will typically download the image once (immediately), and then never download the image again. What is the most commercially feasible method to store the processed images?**
* Store the images on S3 RRS, and create a lifecycle policy to delete the image after 24 hours

**18. You are hosting a website in Ireland called aloud.guru and you decide to have a static DR site available on S3 in the event that your primary site would go down. Your bucket name is also called “acloudguru”. What would be the S3 URL of the static website?**
* https://acloudguru.s3-website-eu-west-1.amazonaws.com

**19. Which of the following is NOT a valid SNS subscribers?**
* SWF

**20. You are appointed as your company's Chief Security Officer and you want to be able to track all changes made to your AWS environment, by all users and at all times, in all regions. What AWS service should you use to achieve this?**
* CloudTrail
