# Section 4 - AWS Object Storage and CDN - S3, Glacier and CloudFront

This section will cover an in-depth overview on the S3 (Simple Storage Service) service.

### What is S3?
* S3 provides developers and IT teams with secure, durable, highly-scalable object storage. Amazon S3 is easy to use, with a simple web services interface to store and retrieve any amount of data from anywhere on the web
* S3 is a safe place to store your files
* S3 is an object-based storage
* The data is spread across multiple devices and facilities

### S3 - The Basics
* S3 is Object-based - i.e. allows you to upload files
* Files can be from 0 Bytes to 5 TB
* There is unlimited storage
* Files are stored in Buckets
* S3 is a universal namespace - names must be unique globally
* URLs look like https://s3-eu-west-1.amazonaws.com/<name>
* When you upload a file to S3 you will receive a HTTP 200 code if the upload was successful

### Data Consistency Model for S3
* Read after Write consistency for PUTS of new Objects
* Eventual Consistency for overwrite PUTS and DELETES (can take some time to propagate)

### S3 is a Simple Key-value Store
Objects consist of the following:
 * Key (this is the name of the object)
 * Value (this is the data and is made up of a sequence of bytes)
 * Version ID (important for versioning)
 * Metadata (Data about data you are storing)
 * Sub resources:
    * Access Control Lists
    * Torrent

### S3 - The Basics (Continued)
* Built for 99.99% availability for the S3 platform.
* Amazon guarantee 99.9% availability
* Amazon guarantee 99.99999999999% durability for S3 information (11 x 9s)
* Tiered storage available
* Lifecycle Management
* Versioning
* Encryption
* Secure your data using Access Control Lists and Bucket Policies

### S3 - Storage Tiers/Classes
* S3 Standard: 99.99% availability, 99.9999999999% durability, stored redundantly across multiple devices in multiple facilities, and is designed to sustain the loss of 2 facilities concurrently
* S3 - IA: (Infrequently Accessed): For data that is accessed less frequently, but requires rapid access when needed. Lower fee than S3 but you are charged a retrieval fee
* S3 One Zone - IA: Want a lower-cost option for infrequently accessed data but do not require the multiple AZ data resilience
* Glacier: Very cheap but used for archival only. Expedited, Standard or Bulk. A standard retrieval time takes 3-5 hours

<div align="center">
  <img src="s3-storage-tiers.jpg">
  <h3>Figure 4-1. S3 Storage classes and info</h3>
</div>

### S3 - Charges
In S3, we are charged for:
* Storage
* Requests
* Storage Management Pricing
* Data Transfer Pricing
* Transfer Acceleration

### What is S3 Transfer Acceleration?
AWS S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your end users and an S3 bucket. Transfer Acceleration takes advantage of AWS CloudFront's globally distributed edge locations. As the data arrives at an edge location, data is routed to AWS S3 over an optimized network path.

### Create and S3 Bucket - Exam Tips
* Buckets are a universal name space
* Upload an object to S3 receives a HTTP 200 code on success
* S3, S3-IA, S3 Reduced Redundancy Storage
* Encryption
  * Client Side Encryption
  * Server Side Encryption
    * Server side encryption with Amazon S3 Managed Keys (SSE-S3)
    * Server side encryption with KMS (SSE-KMS)
    * Server side encryption with Customer Provided Keys (SSE-C)
* Control access to buckets using either a bucket ACL or using Bucket Policies
* **By default buckets are private and all objects stored inside them are private**

### S3 - Versioning Exam Tips
* Stores all versions of an object (including all writes and even if you delete an object)
* Great backup tool
* Once enabled, versioning cannot be disabled, only suspended
* Integrates with Lifecycle rules
* Versioning's MFA Delete capability, which uses multi-factor authentication, can be used to provide an additional layer of security

### S3 - Cross Region Replication Exam Tips
* Versioning must be enabled on both the source and destination buckets
* Regions must be unique
* Files in an existing bucket are not replicated automatically. All subsequent updated files will be replicated automatically
* You cannot replicate to multiple buckets or use daisy chaining
* Delete markers are replicated
* Deleting individual versions or delete markers will not be replicated
* Understand what Cross Region Replication is at a high level

### S3 - Lifecycle Management Lab
* Can be used in conjunction with versioning
* Can be applied to current versions and previous versions
* Following actions can now be done:
  * Transition to the Standard - Infrequent Access Storage Class (30 days after creation date)
  * Archive to the Glacier Storage Class (30 days after IA)
  * Permanently Delete

### What is a CDN?
A CDN (content delivery network) is a system of distributed servers (network) that delivers webpages and other web content to a user based on the geographic locations of the user, the origin of the webpage and a content delivery server.

### CloudFront - Key Terms
* Edge Location - The location where content will be cached. This is separate to an AWS region/AZ
* Origin - The origin of all the files that the CDN will distribute. This can be either an S3 Bucket, an EC2 Instance, and Elastic Load Balancer or Route 53
* Distribution - The name given the CDN which consists of a collection of Edge Locations

### What is CloudFront?
Amazon CloudFront can be used to deliver your entire website, including dynamic, static, streaming, and interactive content using a global network of edge locations. Requests for your content are automatically routed to the nearest edge location, so content is delivered with the best possible performance.

Amazon CloudFront is optimized to work with other services such as S3, EC2, Elastic Load Balancing, and Route 53. CloudFront also works seamlessly with any non-AWS origin server, which stores the original, definitive versions of your files.

### CloudFront - Key Terms (Continued)
* Web Distribution - Typically used for websites
* RTMP - Used for media streaming

### CloudFont - Exam Tips
* Understand the key terms: Edge Location, Origin, Distribution, Web Distribution, and RTMP
* Edge locations are not just READ only, you can write to them too
* Objects are cached for the life of the TTL (time to live)
* You can clear cached objects but you will be charged

### Securing your buckets
* By default, all newly created buckets are **private**
* You can setup access control to your buckets using:
  * Bucket Policies
  * Access Control Lists
* S3 buckets can be configured to create access logs which log all requests made to the S3 bucket. This can be done to another bucket

### Encryption
There are four types of Encryption for S3:
* In transit:
  * SSL/TLS
* At rest:
  * Server Side Encryption
    * S3 Managed Keys - SSE-S3
    * AWS Key Managed Service, Managed Keys - SSE-KMS
    * Server Side Encryption with Customer Provided Keys - SSE-C
  * Client Side Encryption

### Storage Gateway
AWS Storage Gateway is a service that connects an on-premises software appliance with cloud-based storage to provide seamless and secure integration between an organization's on-premises IT environment and AWS's storage infrastructure. The service enables you to securely store data to the AWS cloud for scalable and cost-effective storage.

AWS Storage Gateway's software appliance is available for download as a VM (virtual machine) image that you install on a host in your data center. Storage Gateway supports either VMware ESXi or Microsoft Hyper-V. Once you've installed your gateway and associated it with your AWS account through the activation process, you can use the AWS Management Console to create the storage gateway option that is right for you.

### Four Types of Storage Gateways
* File Gateways (NFS)
* Volumes Gateway (iSCSI)
  * Stored Volumes
  * Cached Volumes
* Tape Gateway (VTL)

### File Gateway
Files are stored as objects in your S3 buckets, accessed through a Network File System (NFS) mount point. Ownership, permissions, and timestamps are durably stored in S3 in the user-metadata of the object associated with the file. Once objects are transferred to S3, they can be managed as native S3 objects, and bucket policies such as versioning, lifecycle management, and cross-region replication apply directly to objects stored in your bucket.

<div align="center">
  <img src="s3-file-gateway.jpg">
  <h3>Figure 4-2. Sample S3 file gateway architecture</h3>
</div>

### Volume Gateway
The volume interface presents your applications with disk volumes using the iSCSI block protocol

Data written to these volumes can be asynchronously backed up as point-in-time snapshots of your volumes, and stored in the cloud as Amazon EBS snapshots.

Snapshots are incremental backups that capture only changed blocks. All snapshot storage is also compressed to minimize your storage charges.

### Volume Gateway - Stored Volumes
Stored volumes let your primary data locally, while asynchronously backing up that data to AWS. Stored volumes provide your on-premises applications with low-latency access to their entire datasets, while providing durable, off-site backups. You can create storage volumes and mount them as iSCSI devices from your on-premises application servers. Data written to your stored volumes is stored on your on-premises storage hardware. This data is asynchronously backed up to S3 in the form of EBS (Amazon Elastic Block Store) snapshots. 1GB - 16 TB in size for Stored Volumes.

<div align="center">
  <img src="volume-gateway-stored-volumes.jpg">
  <h3>Figure 4-3. Sample S3 volume gateway stored volumes architecture</h3>
</div>

### Volume Gateway - Cached Volumes
Cached volumes let you use S3 as your primary data storage while retaining frequently access data locally in your storage gateway. Cached volumes minimize the need to scale your on-premises storage infrastructure, while still providing your applications with low-latency access to their frequently accessed data. You can create storage volumes up to 32 TB in size and attached to them as iSCSI devices from your on-premises application servers. Your gateway stores data that you write to these volumes in S3 and retains recently read data in your on-premises storage gateway's cache and upload buffer storage. 1 GB - 32 TB in size for Cache Volumes

<div align="center">
  <img src="volume-gateway-cached-volumes.jpg">
  <h3>Figure 4-4. Sample S3 volume gateway cached volume architecture</h3>
</div>

### Volume Gateway - Tape Gateway
Tape Gateway offers a durable, cost-effective solution to archive your data in the AWS Cloud. The VTL interface it provides lets your leverage your existing tape-based backup application infrastructure to store data on virtual tape cartridges that you create on your tape gateway. Each tape gateway is preconfigured with a media changer and tape drives, which are available to your existing client backup applications as ISCSI devices. You add tape cartridges as your need to archive your data. Supported by NetBackup, Backup Exec, Veeam etc.

<div align="center">
  <img src="volume-gateway-tape-gateway.jpg">
  <h3>Figure 4-5. Sample S3 volume gateway tape gateway architecture</h3>
</div>

### Storage Gateway - Exam Tips
* File Gateway - For flat files, stored directly on S3
* Volume Gateway:
  * Stored Volumes - Entire dataset is stored on site and is asynchronously backed up to S3
  * Cached Volumes - Entire dataset is stored on S3 and the most frequently accessed data is cached on site
* Gateway Virtual Tape Library (VTL)
  * Used for backup and uses popular backup applications like NetBackup, Backup Exec, Veeam etc.
