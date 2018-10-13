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
