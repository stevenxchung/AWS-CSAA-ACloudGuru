# Section 11: The Well Architected Framework

This section will cover an in-depth overview on AWS Application Services.

### Business Benefits of Cloud
* Almost zero upfront infrastructure investment
* Just-in-time infrastructure
* More efficient resource utilization
* Usage-based costing
* Reduced time to market

### Technical Benefits of Cloud
* Automation - "Scriptable infrastructure"
* Auto-scaling
* Proactive scaling
* More efficient development lifecycle
* Improved testability
* Disaster recovery and business continuity
* "Overflow" the traffic to the cloud

<div align="center">
  <img src="elasticity.jpg">
  <h3>Figure 11-1. Infrastructure cost vs time</h3>
</div>

### Design for Failure
Rule of thumb: be a pessimist when designing architectures in the cloud; assume things will fail. In other words, always design, implement and deploy for automated recovery from failure.

### Decouple Your Components
The key is to build components that do not have tight dependencies on each other, so that if one component were to die, sleep, or reamin busy for some reason, the other components in the system are built so as to continue to work as if no failure is happening.

### Implement Elasticity
The cloud brings a new concept of elasticity in your applications. Elasticity can be implemented in three ways:
1. Proactive cyclic scaling: periodic scaling that occurs at fixed interval (daily, weekly, monthly, quarterly)
2. Proactively event-based scaling: scaling just when you are expecting a big surge of traffic requests due to a scheduled business event (new product launch, marketing campaigns)
3. Auto-scaling based on demand. By using a monitoring service, your system can send triggers to take appropriate actions so that it scales up or down based on metrics (utilization of the servers or network i/o for instance)

### Secure Your Application
Depending on your setup, securing your application is important, see Figure 11-2 on application security at different levels of the application.

<div align="center">
  <img src="secure-app.jpg">
  <h3>Figure 11-2. Application security at different levels</h3>
</div>

### What is a well architected framework?
This has been developed by the Solution Architecture team based on their experience with helping AWS customers. The well architected framework is a set of questions that you can use to evalute how well your architecture is aligned to AWS best practices.

### Five Pillars of The Well-Architected Framework
* Security
* Reliability
* Performance efficiency
* Cost optimization
* Operational excellence

### Structure of each Pillar
* Design principles
* Definition
* Best practices
* Key AWS services
* Resources

### General Design Principles
* Stop guessing your capacity needs
* Test systems at production scale
* Automate to make architectural experimentation easier
* Allow for evolutionary architectures
* Data-driven architectures
* Improve through game days

### Pillar One - Security Design Principles
* Apply security at all layers
* Enable traceability
* Automate responses to security events
* Focus on securing your system
* Automate security best practices

### Pillar One - AWS Shared Responsibility Model
Shown in Figure 11-3 is the AWS shared responsibility model between AWS and the customer. Although the scope of responsibility differs for AWS vs the customer, each party has equal responsibility in securing data.

<div align="center">
  <img src="aws-shared-res.jpg">
  <h3>Figure 11-3. AWS shared responsibility model</h3>
</div>

### Pillar One - Security Definition
Security in the cloud consist of 4 areas:
1. Data protection
2. Privilege management
3. Infrastructure protection
4. Detective controls

### Pillar One - Best Practices - Data Protection
* Before you begin to architect security practices across your environment, basic data classification should be in place. You should organize and classify your data into segments. You should implement a least priviledge access system so that people are only able to access what they need. However, most importantly you should encrypt everything where possible, whether it be at rest or in transit.

* In AWS the following practices help to protect your data:
  * AWS customers maintain full control over their data
  * AWS has designed storage system for exceptional resiliency
  * AWS makes it easier for you to encrypt your data and manage keys, including regular key rotation, which can be easily automated natively by AWS or maintained by a customer
  * Detailed logging is available that contains important content, such as file access and changes
  * Versioning which can be part of a larger data lifecycle management process, can protect against accidental overwrites, deletes, and similar harm
  * AWS never initiates the movement of data between regions. Content is placed in a region will remain in that region unless the customer explicitly enables a feature or leverages a service that provides that functionality

### Pillar One - Best Practices - Data Protection Questions
* How are you encrypting and protecting your data at rest?
* How are you encrypting and protecting your data in transit? (SSL)

### Pillar One - Best Practices - Priviledge Management
Privilege management ensures that only authorized and authenticated users are able to access your resources, and only in a manner that is intended. It can include:
* ACLs (Access Control Lists)
* Role-based access controls
* Password management (such as password rotation policies)

### Pillar One - Best Practices - Priviledge Management Questions
* How are you protecting access to and use of the AWS root account credentials
* How are you defining roles and responsibilities of system users to control human access to the AWS management console and APIs?
* How are you limiting automated access (such as from applications, scripts, or third-party tools or services) to AWS resources?
* How are you managing keys and credentials

### Pillar One - Best Practices - Infrastructure Protection
Outside of cloud, this is how you protect your data center. RFID controls, security, lockable cabinets, CCTV, etc. Within AWS they handle this, so really infrastructure protection exists at a VPC level.

### Pillar One - Best Practices - Infrastructure Protection Questions
* How are you enforcing network and host-level boundary protection?
* How are you enforcing AWS service level protection?
* How are you protecting the integrity of the operating systems on your Amazon EC2 instances?

### Pillar One - Best Practices - Detective Controls
You can use detective controls to detect or identify a security breach. AWS services to achieve this include:
* AWS S3
* AWS Config
* AWs Glacier
* AWS CloudTrail
* AWS CloudWatch

### Pillar One - Best Practices - Detective Controls Questions
* How are you capturing and analyzing AWS logs?

### Pillar One - Key AWS Services
* Data protection
  * You can encrypt you data both in transit and at rest using EBS, S3, and RDS
* Priviledge management
  * IAM, MFA
* Infrastructure protection
  * VPC
* Detective controls
  * AWS CloudTrail, AWS Config, AWS CloudWatch

### Pillar One - Security Exam Tips
Security in the cloud consist of 4 areas:
1. Data protection
2. Privilege management
3. Infrastructure protection
4. Detective controls

Also review each questions section within Pillar One.

### Pillar Two - The Reliability Pillar
The reliability pillar covers the ability of a system to recover from service or infrastructure outages/distruptions as well as the ability to dynamically acquire computing resources to meet demand.

### Pillar Two - Reliability Design Principles
* Test recovery procedures
* Automatically recover from failure
* Scale horizontally to increase aggregate system availability
* Stop guessing capacity

### Pillar Two - Reliability Definition
Reliability in the cloud consists of three areas:
* Foundations
* Change management
* Failure management

### Pillar Two - Best Practices - Foundations
* Before architecting any system, you need to make sure you have the prerequisite foundations. In traditional IT one of the first things you should consider is the size of the comms link between your HQ and your data center. If you misprovision this link, it can take three to six months to upgrade which can cause a huge disruption to your traditional IT estate

* AWS handles most of the foundations for you. The cloud is designed to be essentially limitless meaning that AWS handle the networking can compute requirements themselves. However, they do set service limits to stop customers from accidentally over-provisioning resources

### Pillar Two - Best Practices - Foundations Questions
* How are you managing AWS service limits for you account?
* How are you planning your network topology on AWS?
* Do you have an escalation path to deal with technical issues?

### Pillar Two - Best Practices - Change Management
* You need to be aware of how change affects a system so that you can plan proactively around it. Monitoring allows you to detect any changes to your environment and react. In traditional systems, change control is done manually and are carefully co-ordinated with auditing

* AWS makes things a lot easier, you can use CloudWatch to monitor your environment and services such as autoscaling to automate change in response to changes on your production environment

### Pillar Two - Best Practices - Change Management Questions
* How does your system adapt to changes in demand?
* How are you monitoring AWS resources?
* How are you executing change management?

### Pillar Two - Best Practices - Failure Management
You should always architect your systems with the assumptions that failure will occur. You should become aware of these failures, how they occurred, how to respond to them and then plan on how to prevent these from happening again.

### Pillar Two - Best Practices - Failure Management Questions
* How are you backing up your data?
* How does your system withstand component failures?
* How are you planning for recovery?

### Pillar Two - Key AWS Services
* Foundations
  * IAM, VPC
* Change management
  * AWS CloudTrail
* Failure management
  * AWS CloudFormation

### Pillar Two - Reliability Exam Tips
Reliability in the cloud consists of three areas:
* Foundations
* Change management
* Failure management

Also review each questions section within Pillar Two.
