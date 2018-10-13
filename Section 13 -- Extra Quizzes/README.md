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
* Enable S3 versioning on the bucket & enable Enable Multifactor Authentication (MFA) on the bucket

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
