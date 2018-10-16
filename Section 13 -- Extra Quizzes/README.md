# Section 13: Extra Quizzes

## Mega Quiz 2

**1. You have a high performance compute application and you need to minimize network latency between EC2 instances as much as possible. What can you do to achieve this?**
* Create a placement group with an Availability Zone and place the EC2 instances within that placement group

**2. True or False? Amazon S3 buckets in all Regions provide read-after-write consistency for PUTS of new objects and eventual consistency for overwrite PUTS and DELETES.**
* True

**3. Placement Groups can be created across 2 or more Availability Zones.**
* False

**4. You can add multiple volumes to an EC2 instance and then create your own RAID 5/RAID 10/RAID 0 configurations using those volumes.**
* True

**5. You are creating your own relational database on an EC2 instance and you need to maximize IOPS performance. What can you do to achieve this goal?**
* Add multiple additional volumes with provisioned IOPS and then create a RAID 0 stripe across those volumes

**6. Which of the services below do you get root access to?**
* EC2 & Elastic MapReduce

**7. Using SAML (Security Assertion Markup Language 2.0) you can give your federated users single sign-on (SSO) access to the AWS Management Console.**
* True

**8. You can have 1 subnet stretched across multiple availability zones.**
* False

**9. When you create new subnets within a custom VPC, by default they can communicate with each other, across availability zones.**
* True

**10. It is possible to transfer a reserved instance from one Availability Zone to another.**
* True

**11. You have an EC2 instance which needs to find out both its private IP address and its public IP address. To do this you need to:**
* Retrieve the instance Metadata from http://169.254.169.254/latest/meta-data/

**12. To retrieve instance metadata or user data you will need to use the following IP Address:**
* http://169.254.169.254

**13. Amazon S3 buckets in all regions provide read-after-write consistency for PUTS of new objects.**
* True

**14. Amazon S3 buckets in all regions do not provide eventual consistency for overwrite PUTS and DELETES.**
* False

**15. Amazon S3 provides:**
* Unlimited Storage

**16. In order to enable encryption at rest using EC2 and Elastic Block Store you need to:**
* Configure encryption when creating the EBS volume

**17. You can select a specific Availability Zone in which to place your DynamoDB Table**
* False

**18. When creating an RDS instance you can select which availability zone in which to deploy your instance.**
* True

**19. Amazon's Redshift uses which block size for its columnar storage?**
* 1024 KB / 1 MB

**20. You run a website which hosts videos and you have two types of members, premium fee paying members and free members. All videos uploaded by both your premium members and free members are processed by a fleet of EC2 instances which will poll SQS as videos are uploaded. However you need to ensure that your premium fee paying members videos have a higher priority than your free members. How do you design SQS?**
* Create two SQS queues, one for premium members and one for free members. Program your EC2 fleet to poll the premium queue first and if empty, to then poll your free members SQS queue

**21. You have uploaded a file to S3. What HTTP code would indicate that the upload was successful?**
* HTTP 200

**22. You are hosting a MySQL database on the root volume of an EC2 instance. The database is using a large amount of IOPS and you need to increase the IOPS available to it. What should you do?**
* Add 4 additional EBS SSD volumes and create a RAID 10 using these volumes

## Scenario Based Questions

**1. You have been asked to create VPC for your company. The VPC must support both Internet-facing web applications (i.e. they need to be publicly accessible) and internal private applications (i.e. they are not publicly accessible and can be accessed only over VPN). The internal private applications must be inside a private subnet. Both the internet-facing and private applications must be able to leverage at least three Availability Zones for high availability. At a minimum, how many subnets must you create within your VPC to achieve this?**
* 6

**2. You work for a cosmetic company which has their production website on AWS. The site itself is in a two-tier configuration with web servers in the front end and database servers at the back end. The site uses using Elastic Load Balancing and Auto Scaling. The databases maintain consistency by replicating changes to each other as and when they occur. This requires the databases to have extremely low latency. Your website needs to be highly redundant and must be designed so that if one availability zone goes offline and Auto Scaling cannot launch new instances in the remaining Availability Zones the site will not go offline. How can the current architecture be enhanced to ensure this?**
* Deploy your site in three different AZ's within the same region. Configure the Auto Scaling minimum to handle 50 percent of the peak load per zone

**3. You working in the media industry and you have created a web application where users will be able to upload photos they create to your website. This web application must be able to call the S3 API in order to be able to function. Where should you store your API credentials whilst maintaining the maximum level of security.**
* Don't save your API credentials. Instead create a role in IAM and assign this role to an EC2 instance when you first create it

**4. You are a systems administrator and you need to monitor the health of your production environment. You decide to do this using Cloud Watch, however you notice that you cannot see the health of every important metric in the default dash board. Which of the following metrics do you need to design a custom cloud watch metric for, when monitoring the health of your EC2 instances?**
* Memory usage

**5. You are a student currently learning about the different AWS services. Your employer asks you to tell him a bit about Amazon's glacier service. Which of the following best describes the use cases for Glacier?**
* Infrequently accessed data & data archives

**6. You work for a toy company that has a busy online store. As you are approaching Christmas, you find that your store is getting more and more traffic. Your web tier is behind an Auto Scaling group, but you notice that it is frequently scaling, sometimes multiple times in an hour, only to scale back down after peak usage. You need to keep Auto Scaling from scaling up and down so rapidly. Which of the following options would help you to achieve this?**
* Modify the Auto Scaling group cool-down timers & modify the Amazon CloudWatch alarm period that triggers your Auto Scaling scale down policy

**7. You work in the genomics industry and you process large amounts of genomic data using a nightly Elastic Map Reduce (EMR) job. This job processes a single 3 Tb file which is stored on S3. The EMR job runs on 3 on-demand core nodes and four on-demand task nodes. The EMR job is now taking longer than anticipated and you have been asked to advise how to reduce the completion time?**
* You should reduce the input split size in the MapReduce job configuration and then adjust the number of simultaneous mapper tasks so that more tasks can be processed at once

**8. By definition a public subnet within a VPC is one that:**
* In its routing table it has at least one route that uses an Internet Gateway (IGW)

**9. You have been asked to identify a service on AWS that is a durable key value store. Which of the services below meets this definition?**
* Simple Storage Service (S3)

**10. You are a security architect working for a large antivirus company. The production environment has recently been moved to AWS and is in a public subnet. You are able to view the production environment over HTTP however when your customers try to update their virus definition files over a custom port, that port is blocked. You log in to the console and you allow traffic in over the custom port. How long will this take to take effect?**
* Immediately

**11. You are a solutions architect working for a biotech company who is pioneering research in immunotherapy. They have developed a new cancer treatment that may be able to cure up to 94% of cancers. They store their research data on S3, however recently an intern accidentally deleted some critical files. You've been asked to prevent this from happening in the future. What options below can prevent this?**
* Enable S3 versioning on the bucket & enable Multifactor Authentication (MFA) on the bucket

**12. You run an automobile reselling company that has a popular online store on AWS. The application sits behind an Auto Scaling group and requires new instances of the Auto Scaling group to identify their public and private IP addresses. How can you achieve this?**
* Using a Curl or Get Command to get the latest meta-data from http://169.254.169.254/latest/meta-data/

**13. You are a solutions architect who has been asked to do some consulting for a US company that produces re-useable rocket parts. They have a new web application that needs to be built and this application must be stateless. Which three services could you use to achieve this?**
* RDS, DynamoDB & ElastiCache

**14. Your company has decided to set up a new AWS account for test and dev purposes. They already use AWS for production, but would like a new account dedicated for test and dev so as to not accidentally break the production environment. You launch an exact replica of your production environment using a CloudFormation template that your company uses in production. However CloudFormation fails. You use the exact same CloudFormation template in production so the failure is something to do with your new AWS account. The CloudFormation template is trying to launch 60 new EC2 instances in a single availability zone. After some research you discover that the problem is:**
* For all new AWS accounts there is a soft limit of 20 EC2 instances per region. You should submit the limit increase form and retry the template after your limit has been increased

**15. You work for a famous bakery who are deploying a hybrid cloud approach. Their legacy IBM AS400 servers will remain on premise within their own datacenter however they will need to be able to communicate to the AWS environment over a site to site VPN connection. What do you need to do to establish the VPN connection?**
* Assign a public IP address to your Amazon VPC Gateway

**16. You work for a major news network in Europe. They have just released a new app which allows users to report on events as and when they happen using their mobile phone. Users are able to upload pictures from the app and then other users will be able to view these pics. Your organization expects this app to grow very quickly, essentially doubling its user base every month. The app uses S3 to store the media and you are expecting sudden and large increases in traffic to S3 when a major news event takes place (as people will be uploading content in huge numbers). You need to keep your storage costs to a minimum however and it does not matter if some objects are lost. Which storage media should you use to keep costs as low as possible?**
* S3 - Reduced Redundancy Storage (RRS)

**17. You have developed a new web application in us-west-2 that requires six Amazon Elastic Compute Cloud (EC2) instances running at all times. You have three availability zones available in that region (us-west-2a, us-west-2b, and us-west-2c). You need 100 percent fault tolerance if any single Availability Zone in us-west-2 becomes unavailable. How would you do this, each answer has 2 answers, select the answer with BOTH correct answers.**
* Answer 1 - Us-west-2a with six EC2 instances, us-west-2b with six EC2 instances, and us-west-2c with no EC2 instances. Answer 2 - Us-west-2a with three EC2 instances, us-west-2b with three EC2 instances, and us-west-2c with three EC2 instances

**18. You need to add a route to your routing table in order to allow connections to the internet from your subnet. What route should you add?**
* Destination: 0.0.0.0/0 --> Target: your Internet gateway

**19. You work for a construction company that has their production environment in AWS. The production environment consists of 3 identical web servers that are launched from a standard Amazon Linux AMI using Auto Scaling. The web servers are launched in to the same public subnet and belong to the same security group. They also sit behind the same ELB. You decide to do some test and dev and you launch a 4th EC2 instance in to the same subnet and same security group. Annoyingly your 4th instance does not appear to have internet connectivity. What could be the cause of this?**
* Assign an elastic IP address to the fourth instance

**20. With which AWS orchestration service can you implement Chef recipes?**
* OpsWorks

## Final Practice Exam

**1. You are a solutions architect working for a large pharmaceutical company who are involved in high performance computing to develop new drugs to treat arthritis. You are helping them to design a new application which will need to keep network traffic the lowest latency possible while leveraging very high CPU performance. They would like to place this solution on to the AWS platform and are looking for your recommendations. Which of the following do you suggest?**
* CPU optimized EC2 instances deployed into placement groups

**2. You work for an automotive company which is migrating their production environment in to AWS. The company has 4 separate segments, Dev, Test, UAT & Production. They require each segment to be logically isolated from each other. What VPC configuration should you recommend?**
* A separate VPC for each segment. Then create VPN tunnels from your HQ to each VPC so the appropriate teams can each speak to their dedicated VPC

**3. By default how many VPCs can you have per region in your AWS account?**
* 5

**4. Which of the following is not associated with Identity Access Management Service?**
* Workspaces

**5. You are designing a new application for a financial company that will utilize spot EC2 instances as and when they meet a certain price point. These EC2 instances will analyze data and the output their analysis to the root volume. You need to store this data in a persistent form of storage so that if the spot instances are terminated by Amazon, you will not lose your data. You need to choose the lowest cost service. Where should you store your data?**
* S3

**6. Which of the following is not a responsibility of Amazon’s under the shared responsibility model?**
* OS level patching for EC2

**7. In regards to EC2 which of the following is not a customer’s responsibility under the shared responsibility model?**
* Decommissioning and destruction of storage media

**8. Which of the following is true when writing to S3?**
* All regions provide read-after-write consistency for PUTS of new objects in your Amazon S3 bucket and eventual consistency for overwrite PUTS and DELETES

**9. You are solutions architect working for a busy ecommerce store. Due to your organizations unique security requirements, you decide to utilize EC2 running a MySQL database, rather than using RDS. You need to architect this EC2 instance to maximize your disk IO. Which of the following would give you the best disk performance?**
* Add 2 x additional PIOPS SSD volumes and create a RAID 0. Install MySQL to this RAID 0 partition

**10. Which of the following services do you get OS level access to?**
* EC2 & Elastic Map Reduce (EMR)

**11. You are designing an AWS solution for a new customer and they want to use their active directory credentials in order to sign in to the AWS management console. What kind of authentication response is required in order for users to authenticate with the AWS security token service (STS).**
* Security Assertion Markup Language 2.0 (SAML 2.0)

**12. You are designing a new VPC for a customer and you need to deploy your EC2 instances in to multiple availability zones. What is the minimum number of subnets that you require to achieve this objective?**
* 2 Subnets with each subnet in an independent AZ

**13. You are creating a new VPC with 3 subnets in 3 separate availability zones. You require instances in each subnet to be able to communicate to each other by default. What additional steps should you take in order to achieve this objective.**
* You do not need to do anything, by default all subnets can communicate with each other using the main route table

**14. You have an EC2 instance which needs to find out both its private IP address and its public IP address using a script. Which of the below should you include in the script to discover this information.**
* Retrieve the instance Metadata from http://169.254.169.254/latest/meta-data/

**15. You are an AWS architect and you require encryption at rest for additional volumes attached to your EC2 instance. What is the quickest and most efficient way to achieve this?**
* Configure encryption when creating the EBS volume

**16. You are designing a web application for a new social media start up and have recommended using DynamoDB for the database due to its superior performance. You need to ensure that your database has redundancy. What additional steps should you do?**
* Nothing, DynamoDB all data is automatically replicated across multiple availability zones

**17. What block size does Redshift use when storing its data in columnar storage?**
* 1024 KB

**18. You are designing an application for a furniture retailer. A component of the application takes pictures of the furniture for sale and generates thumb nail images which then need to be stored persistently. The business can tolerate it if some images are lost as they can be regenerated. The thumbnails will need to be retrieved immediately when the application requests them. What is the cheapest option to do this?**
* Using S3 RRS

**19. You run a website which hosts videos and you have two types of members, premium fee paying members and free members. All videos uploaded by both your premium members and free members are processed by a fleet of EC2 instances which will poll SQS as videos are uploaded. However you need to ensure that your premium fee paying members videos have a higher priority than your free members. How should you design your application.**
* Create two SQS queues, one for premium members and one for free members. Program your EC2 fleet to poll the premium queue first and if empty, to then poll your free members SQS queue

**20. You are designing an image sharing website that will distribute images across the world. You need to maximize performance so that your end users can download frequently accessed images as fast as possible. What AWS technology should you implement?**
* CloudFront

**21. You are putting together a WordPress site for a local charity and you are using a combination of Route 53, Elastic Load Balancers, EC2 & RDS. You launch your EC2 instance, download WordPress and setup the configuration files connection string so that it can communicate to RDS. When you browse to your URL however, nothing happens. Which of the following could NOT be the cause of this?**
* You have locked port 22 down to your specific IP address therefore users cannot access your site using HTTP/HTTPS

**22. You have uploaded a file to S3, what HTTP code would indicate that the upload was successful?**
* HTTP 200

**23. You have created a custom VPC with 3 subnets, 2 private, 1 public. You deploy 3 EC2 instances in to your public subnet and attach Elastic IP addresses to these instances. You then deploy an EC2 instance in to your private subnet and then attempt to apply security patches to this instance, however it has no internet connectivity. What can you do to give this instance internet access?**
* Deploy a NAT to the public subnet and then update the main route table to send traffic via the NAT to the private subnet

**24. Amazon SWF is designed to help users to do which of the following?**
* Coordinate synchronous and asynchronous tasks

**25. What service can you use to audit user access & API calls across your AWS environment?**
* CloudTrail

**26. Under the shared responsibility model for S3 which of the following is NOT a responsibility of Amazons?**
* Configuration of individual bucket policies

**27. Under the shared responsibility model for DynamoDB which of the following is NOT a responsibility of Amazons?**
* Restricting access of DynamoDB so that only the customers web application in EC2 can write data to it

**28. You are a Solutions Architect working for a major European oil company. You are designing a new web application which will need to access data stored in DynamoDB. You need to do this as securely as possible, without storing any credentials on a long term basis. How would you achieve this?**
* Use AWS Identity and Access Management roles for the EC2 Instances that need to make the API calls

**29. You are a solutions architect working for a large cell phone company in the US. Your CSO has engaged a third party security company to conduct a security audit of your company to make sure it is not liable to hacking. The third party security company would like to conduct a penetration test on your AWS estate. Would this be allowed by AWS?**
* Yes, however you need to get permission from Amazon first by raising a ticket

**30. AWS help provide protection against some forms of traditional network attacks. Which of the following is not protected against by AWS?**
* Social Engineering

**31. Placement Groups can be created across 2 or more Availability Zones.**
* False, Placement Groups are restricted to a single Availability Zone

**32. You have three AWS accounts (A, B & C) which share data.  In an attempt to maximize performance between the accounts, you deploy the instances owned by these three accounts in "eu-west-1b".  During testing, you find inconsistent results in transfer latency between the instances. Transfer between accounts A and B is excellent, but transfers between accounts B and C, and C and A, are slower. What could be the problem?**
* The names of the AZs are randomly applied, so 'eu-west-1b' is not necessarily the same physical location for all three accounts

**33. Your company has hired a young and enthusiastic accountant. After reviewing the AWS documentation and usage graphs, he announces that you are wasting vast amounts of money running servers for a full hour instead of spinning them up only when they are needed and down again as soon as they are idle for 1 minute. He cites the AWS claim that you only pay for what you use, and that as a senior engineer, you should be more conscious of wasting company money. How do you respond?**
* You thank him for his concern, and advise him that he has misinterpreted the pricing document: Instances are billed by the full hour, and partial hours are billed as such.  Additionally, storage charges are incurred even if the Db instance sits idle. Taking into account productivity losses, stopping and restarting Db instances may actually result in additional costs. As such, your solution is fine as it now stands.

**34. Your company is moving their 10TB data warehouse to the cloud. Taking into account your company's 100Mbps connection, which service would most quickly get your data into AWS?**
* Amazon Snowball

**35. You have been monitoring a sensitive auto scaling group, and you expect it to scale-in as you enter a period of holiday downtime. The auto scaling group is distributed over three AZs (AZ - A & -B have two instances each, and AZ -C has three instances). All instances have different CPU and Memory utilization, and all instances have been running for a different number of days. All instances come from different versions of a root AMI, and all instances have different numbers of sessions connected. Which instance will be the 1st to shut down?**
* The instance in AZ -C that has the oldest launch configuration will terminate first, Auto Scaling scales-in according to a hierarchy of decisions. Please see the link for further details: http://amzn.to/2lSm9k6

**36. Auto Scaling is a tool used to create fault-tolerant and cost-effective architectures.**
* True, auto scaling improves availability and will keep your infrastructure at the size needed to run your application

**37. What is the maximum Visibility Timeout of an SQS message in a FIFO queue?**
* 12 hours

**38. A client who is using EC2 believes that someone other than approved administrators is trying to gain access to her Linux web app instances, and she asks what sort of network access logging can be added to the system. Which of the following might you recommend?**
* Make use of an OS level logging tools such as IP tables and log events to CloudWatch or S3

**39. Your company likes the idea of storing files on AWS. However, low-latency service of the last few days of files is important to customer service. Which Storage Gateway configuration would you use to achieve both of these ends?**
* Gateway-Cached volumes - retain a copy of frequently accessed data subsets locally. Cached volumes offer a substantial cost savings on primary storage and minimize the need to scale your storage on-premises

**40. You have a MySQL database running on an EC2 instance in a private subnet. You can connect via SSH, but you are unable to apply updates to the database server via the NAT instance. What might you do to remedy this problem?**
* Ensure that "Source/Destination Checks" is disabled on the NAT instance

**41. Amazon SQS keeps track of all tasks and events in an application.**
* False, with SQS, you must implement your own application-level tracking, especially if your application uses multiple queues

**42. When editing permissions (policies and ACLs), to whom does the concept of the "Owner" refer?**
* The "Owner" refers to the identity and email address used to create the account AWS account

**43. Your company provides an online image recognition service and uses SQS to decouple system components. Your EC2 instances poll the image queue as often as possible to keep end-to-end throughput as high as possible, but you realize that all this polling is resulting in both a large number of CPU cycles and skyrocketing costs. How can you reduce cost without compromising service?**
* Enable long polling by setting the ReceiveMessageWaitTimeSeconds to a number > 0.  SQS long polling doesn’t return a response until a message arrives in the queue, reducing your overall cost over time. Short polling WILL return empty responses

**44. You need to store some easily-replaceable objects on S3. With quick retrieval times and cost effectiveness in mind, which S3 storage class should you consider.**
* S3 - RRS, you should use S3 - RRS. You want to minimize your retrieval time, so you should not use Glacier (and there is no such thing as S3 - Provisioned IOPS)

**45. You are a solutions architect working for a busy media company with offices in Japan and the United States. Your production environment is hosted both in US-EAST-1 and AP-NORTHEAST-1. Your European users have been connecting to the production environment in Japan, and are seeing the site in Japanese rather than in English. You need to ensure that they view the English language version. Which of the routing policies below could help you achieve this?**
* Geolocation, the aim is to direct sessions to the host that will provide the correct language. Geolocation is the best option because it is deterministic. While latency-based routing will usually direct the client to the correct host, connectivity issues with the US Regions might direct traffic to AP. In this case, the word \"ensure\" is operative: users MUST connect to the English-language site. Watch the wording in the exam: a requirement may be presented very casually in the wording of the question. However, understanding that requirement is mandatory if you're going to arrive at the correct answer

**46. Although your application customarily runs at 30% usage, you have identified a recurring usage spike (>90%) between 8pm and midnight daily. What is the most cost effective way to scale your application to meet this increased need?**
* Use Proactive Cyclic Scaling to boost your capacity at a fixed interval

**47. You work for a popular media outlet about to release a story that is expected to go viral. During load testing on the website, you discover that there is read contention on the database tier of your application. Your RDS instance consists of a MySQL database on an extra-large instance. Which two of the following approaches would be best to further scale this instance to meet the anticipated increase in traffic your viral story will generate?**
* Use ElastiCache to cache the frequently read, static data

**48. Following advice from your consultant, you have configured your VPC to use dedicated hosting tenancy. A subsequent change to your application has rendered the performance gains from dedicated tenancy superfluous, and you would now like to recoup some of these greater costs. How do you revert to Default hosting tenancy?**
* Create AMIs of all your instances. Create a new VPC with Default as the hosting tenancy attribute, and use them to create new instances using Default tenancy

**49. Which URL format does S3 support in pointing to bucket "mynewbucket"?**
* http://mynewbucket.s3-aws-region.amazonaws.com

**50. You are developing a web application, and you are maintaining separate sets of resources for your alpha, beta, and release environments. Each version runs on Amazon EC2 with an EBS volume. You use Elastic Load Balancing to manage traffic and Amazon Route 53 to manage your domain. What's the best way to check the health and status of all three groups of services simultaneously?**
* Create a resource group containing each set of resources and view all three environments from a single, group dashboard

**51. Your company has just purchased another company. As part of the merger, your team has been instructed to cross connect the corporate networks. You run all your confidential corporate services and Internal DNS in a VPC. The merged company has all their confidential corporate services and Internal DNS on-premises. After establishing a Direct-Connect service between your VPC and their on premise network, and confirming all the routing, firewalls, and authentication, you find that while you can resolve names against their DNS, the other company services is unable to resolve names against your DNS servers. Why might this be?**
* By design, AWS DNS does not respond to requests originating from outside the VPC

**52. How is the Public IP address managed in an instance session via the instance GUI/RDP or Terminal/SSH session?**
* The Public IP address is not managed on the instance: It is, instead, an alias applied as a network address translation of the Private IP address

**53. You have been engaged by a company to design and lead a migration to an AWS environment. The team is concerned about the capabilities of the new environment, especially when it comes to avoiding bottlenecks. The design calls for about 20 instances (C3.2xLarge) pulling jobs/messages from SQS. Network traffic per instance is estimated to be around 500 Mbps at the beginning and end of each job. Which network configuration should you plan on deploying?**
* Spread the Instances over multiple AZs to minimize the traffic concentration and maximize the fault tolerance

**54. You are a consultant planning to deploy DynamoDB across three AZs. Your lead DBA is concerned about data consistency. Which of the following do you advise the lead DBA to do?**
* To ask the development team to code for strongly consistent reads. As the consultant, you will advise the CTO of the increased cost

**55. You successfully configure VPC Peering between VPC-A and VPC-B. You then establish an IGW and a Direct-Connect connection in VPC-B. Can instances in VPC-A connect to your corporate office via the Direct-Connect service, and connect to the Internet via the IGW?**
* VPC peering does not support edge to edge routing

**56. You are reviewing Change Control requests, and you note that there is a change designed to reduce wasted CPU cycles by increasing the value of Visibility Timeout attribute. What does this mean?**
* When a consumer instance retrieves a message, that message will be hidden from other consumer instances for a fixed period

**57. You manage a Ruby on Rails application that lives on a cluster of EC2 instances. Your website occasionally experiences brief, strong, and entirely unpredictable spikes in traffic that overwhelm your EC2 instances’ resources and freeze the application. As a result, you're losing recently submitted requests from end users. You use Auto Scaling to deploy additional resources to handle the load during spikes, but the new instances don't spin-up fast enough to prevent the existing application servers from freezing. Which of the following will provide the most cost-effective solution in preventing the loss of recently submitted requests?**
* Use Amazon SQS to decouple the application components and keep the requests in queue until the extra Auto-Scaling instances are available. Neither increasing the size of your EC2 instances nor maintaining additional EC2 instances is cost-effective, and pre-warming an ELB signifies that these spikes in traffic are predictable. The cost-effective solution to the unpredictable spike in traffic is to use SQS to decouple the application components

**58. You're building out a single-region application in us-west-2. However, disaster recovery is a strong consideration, and you need to build the application so that if us-west-2 becomes unavailable, you can fail-over to us-west-1. Your application relies exclusively on pre-built AMI's. In order to share those AMI's with the region you're using as a backup, which process would you follow?**
* Copy the AMI from us-west-2, manually apply launch permissions, user-defined tags, and Amazon S3 bucket permissions of the default AMI to the new instance, and launch the instance. AWS does not copy launch permissions, user-defined tags, or Amazon S3 bucket permissions from the source AMI to the new AMI

**59. At the monthly product meeting, one of the Product Owners proposes an idea to address an immediate shortcoming of the product system: storing a copy of the customer price schedule in the customer record in the database. You know that you can store large text or binary objects in DynamoDB. You give a tentative OK to do a Minimal Viable Product test, but stipulate that it must comply with the size limitation on the Attribute Name & Value. Which is the correct limitation?**
* The Name must not exceed 64 KB and the Value must not exceed 255 KB

**60. To save money, you quickly stored some data on the root volume of an EC2 instance and shut it down for the weekend. When you returned on Monday and restarted your instance, you discovered that your data was gone. Why might that be?**
* The root volume was ephemeral, block-level storage. Data on an instance store volume is lost if an instance terminates. The most likely answer is that the EC2 instance was backed by an instance store volume. Instance store volumes are ephemeral, meaning that they exist ONLY in conjunction with their accompanying EC2 instance.
