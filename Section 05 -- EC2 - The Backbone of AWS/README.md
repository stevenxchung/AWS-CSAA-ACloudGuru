# Section 5: EC2 - The Backbone of AWS

This section will cover an in-depth overview on the AWS Elastic Compute Cloud (EC2) service.

### What is EC2?
Amazon EC2 (Elastic Cloud Compute) is a web service that provides resizable compute capacity in the cloud. Amazon EC2 reduces the time required to obtain and boot new server instances to minutes, allowing you to quickly scale capacity, both up and down, as your computing requirements change.

EC2 changes the economics of computing by allowing you to pay only for capacity that you actually use. EC2 provides developers the tools to build failure resilient applications and isolate themselves from common failure scenarios.

### EC2 Options
* On Demand - Allows you to pay a fixed rate by the hour (or by the second) with no commitment
* Reserved - Provides you with a capacity reservation and offers a significant discount on the hourly charge for an instance. 1 year or 3 year terms
* Spot - Enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times
* Dedicated Hosts - Physical EC2 server dedicated for you use. Dedicated Hosts can help you reduce costs by allowing you to use your existing server-bound software licenses

### On Demand
* Perfect for users that want the low cost and flexibility of EC2 without any up-front payment or long-term commitment
* Applications with short term, spiky, or unpredictable workloads that cannot be interrupted
* Applications being developed or tested on EC2 for the first time

### Reserved
* Applications with steady state or predictable usage
* Applications that require reserved capacity
* Users can make up-front payments to reduce their total computing costs even further
  * Standard RIs (up to 75% off on-demand)
  * Convertible RIs (up to 54% off on-demand) feature the capability to change the attributes of the RI as long as the exchange results in the creation of Reserved Instances of equal or greater value
  * Schedule RIs are available to launch within the time window you reserve. This option allows you to match your capacity reservation to a predictable recurring schedule that only requires a fraction of a day, week, or month

### Spot
* Applications that have flexible start and end times
* Applications that are only feasible at very low compute prices
* Users with an urgent need for large amounts of additional computing capacity

### Dedicated Hosts
* Useful for regulatory requirements that may not support multi-tenant virtualization
* Great for licensing which does not support multi-tenancy or cloud deployments
* Can be purchased on-demand (hourly)
* Can be purchased as a Reservation for up to 70% off the on-demand price

### EC2 Instance Types

<div align="center">
  <img src="specialities-use-cases.jpg">
  <h3>Figure 5-1. EC2 instance types, specialties and use cases</h3>
</div>

### What is EBS?
Amazon EBS (Elastic Block Storage) allows you to create storage volumes and attach them to EC2 instances. Once attached, you can create a file system on top of these volumes, run a database, or use them in any other way you would use a block device. EBS volumes are placed in a specific AZ where they are automatically replicated to protect you from the failure of a single component.

### EBS Volume Types
* General Purpose SSD (GP2)
  * General purpose, balances both price and performance
  * Ratio of IOPS per GB with up to 10,000 IOPS and the ability to burst up to 300 IOPS for extended periods of time for volumes at 3334 GB and above
* Provisioned IOPS SSD (101)
  * Designed for I/O intensive applications such as large relational or NoSQL databases
  * Use if you need more than 10,000 IOPS
  * Can provision up to 20,000 IOPS per volume
* Throughput Optimized HDD (ST1)
  * Big data
  * Data warehouses
  * Log processing
  * Cannot be a boot volume
* Cold HDD (SC1)
  * Lowest cost storage for infrequently accessed workloads
  * File server
  * Cannot be a boot volume
* Magnetic (Standard)
* Lowest cost per GB of all EBS volume types that is bootable. Magnetic volumes are ideal for workloads where data is accessed infrequently, and applications where the lowest storage cost is important

### EC2 Exam Tips
* Know On-Demand, Reserved, Spot, and Dedicated Host EC2 services
* If a Spot instance is terminated by EC2, you will not be charged for a partial hour of usage. However, if you terminate the instance yourself, you will be charged for the complete hour in which the instance ran
* Know FIGHT DR MC PX acronym (EC2 instance types, specialties and use cases)
* SSD:
  * General Purpose SSD - Balance price and performance for a wide variety of workloads
  * Provisioned IOPS SSD - Highest performance SSD volume for mission-critical low-latency or high-throughput workloads

* Magnetic:
  * Throughput Optimized HDD - Low cost HDD volume designed for frequently accessed, throughput-intensive workloads
  * Cold HDD - Lowest cost HDD volume designed for less frequently accessed workloads
  * Magnetic - Previous generation. Can be boot volume

### EC2 Lab Summary
* Termination Protection is turned off by default, you must turn it on
* On an EBS-backed instance, the default action is for the root EBS volume to be deleted when the instance is terminated
* EBS root volumes of your DEFAULT AMI's cannot be encrypted. You can also use a third party tool (such as bit locker) to encrypt the root volume, or this can be done when creating AMI's in the AWS console or using the API

### Security Group Basics
* All inbound traffic is blocked by default
* All outbound traffic is allowed
* Changes to security groups take effect immediately
* You can have any number of EC2 instances within a security group
* You can have multiple security groups attached to EC2 instances
* Security groups are STATEFUL (network access control lists are STATELESS):
  * If you create an inbound rule allowing traffic in, that traffic is automatically allowed back out again
* You cannot block specific IP addresses using security groups, instead use Network Access Control Lists
* You can specify allow rules but not deny rules

### Volumes and Snapshots
* Volumes exist on EBS:
  * Virtual Hard Disk
* Snapshots exist on S3
* Snapshots are point in time copies of volumes
* Snapshots are incremental - this means that only the blocks that have changed since your last snapshot are moved to S3

### Snapshots of Root Device Volumes
* To create a snapshot for EBS volumes that serve as root devices, you should stop the instance before taking the snapshot
* However, you can take while the instance is running
* You can create AMI's from EBS-backed instances and snapshots
* You can change EBS volume sizes on the fly, including changing the size and storage type
* Volumes will ALWAYS be in the same AZ as the EC2 instance
* To move an EC2 volume from one AZ/Region to another, take a snap or an image of it, then copy it to the new AZ/Region

### Volume vs Snapshots - Security
* Snapshots of encrypted volumes are encrypted automatically
* Volumes restored from encrypted snapshots are encrypted automatically
* You can share snapshots, but only if they are unencrypted
  * These snapshots can be shared with other AWS accounts or made public

### RAID, Volumes and Snapshots
* RAID - Redundant Array of Independent Disks
  * RAID 0 - Striped, No Redundancy, Good Performance
  * RAID 1 - Mirrored, Redundancy
  * RAID 5 - Good for reads, bad for writes, AWS does not recommend ever putting RAID 5's on EBS
  * RAID 10 - Striped and Mirrored, Good Redundancy, Good Performance

### Snapshots of a RAID array
* Problem - Take a snapshot, the snapshot excludes data held in the cache by applications and the OS. This tends not to matter on a single volume, however using multiple volumes in a RAID array, this can be a problem due to interdependencies of the array
* Solution - Take an application consistent snapshot
  * Stop the application from writing to disk
  * Flush all caches to the disk
  * Ways to accomplish these tasks above:
    * Freeze the file system
    * Unmount the RAID array
    * Shutting down the associated EC2 instance

### EBS vs Instance Store
* All AMIs are categorized as either backed by EBS or backed by instance store
* For EBS volumes - The root device for an instance launched from the AMI is an EBS volume created from an EBS snapshot
* For instance store volumes - The root device for an instance launched from the AMI is an instance store volume created from a template stored in S3

### EBS vs Instance Store - Exam Tips
* Instance store volumes are sometimes called Ephemeral Storage
* Instance store volumes cannot be stopped. If the underlying host fails, you lose your data
* EBS backed instance can be stopped. You will not lose the data on this instance if it is stopped
* You can reboot both, you will not lose your data
* By default, both ROOT volumes will be deleted on termination, however with EBS volumes, you can tell AWS to keep the root device volume

### Types of Load Balancers
Three types of load balancers:
* Application load balancer - Are best suited for load balancing of HTTP and HTTPS traffic. They operate at Layer 7 and are application-aware. They are intelligent, and you can create advanced request routing, sending specified requests to specific web servers
* Network load balancer - Are best suited for load balancing of TCP traffic where extreme performance is required. Operating at the connection level (Layer 4), network load balancers are capable of handling millions of requests per second, while maintaining ultra-low latencies. Use for extreme performance
* Classic load balancer - Are the legacy ELB (Elastic Load Balancers). You can load balance HTTP/HTTPS applications and use Layer 7-specific features, such as X-Forwarded and sticky sessions. You can also use strict Layer 4 load balancing for applications that rely purely on the TCP protocol

### Load Balancer Errors
* Classic Load Balancers - If your application stops responding the ELB responds with a 504 error. This means that the application is having issues. This could be either at the Web Server layer or at the Database Layer. Identify where the application is failing and scale it up or out where possible

### ELB Exam Tips
* 3 types of load balancers:
  * Application load balancers
  * Network load balancers
  * Classic load balancers
* 504 error means that the gateway has timed out. This means that the application not responding within the idle timeout period.
  * Trouble shoot the application. Is it the Web Server or Database Server?
* If you need the IPv4 address of your end user, look for the X-Forwarded-For-Header

### Elastic Load Balancers Lab
* Instances monitored by ELB are reported as “In Service” or “Out of Service”
* Health Checks - Check the instance health by talking to it
* ELBs have their own DNS name. You are never given an IP address
* Read the ELB FAQ for Classic Load Balancers

### CloudWatch EC2 Lab
* Standard Monitoring - 5 minute
* Detailed Monitoring - 1 minute
* What can I do with CloudWatch?
  * Dashboards - Create awesome dashboards to see what is happening with your AWS environment
  * Alarms - Allows you to set Alarms that notify you when particular thresholds are hit
  * Events - CloudWatch events helps you respond to state changes in your AWS resources
  * Logs - CloudWatch logs helps you aggregate, monitor, and store logs
