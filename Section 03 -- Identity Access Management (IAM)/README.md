# Section 3: Identity Access Management (IAM)

This section will cover an in-depth overview on the IAM service.

### IAM Overview
* Centralized control of your AWS account
* Shared Access to your AWS account
* Identity Federation (including Active Directory, Facebook, LinkedIn, etc.)
* Multifactor Authentication
* Provide temporary access for users/devices and services where necessary
* Allows you to set up your own password rotation policy
* Integrates with many different AWS services
* Supports PCI DSS Compliance

### Critical Terms
* Users - End Users
* Groups - A collection of users under one set of permissions
* Roles - You create roles and can then assign them to AWS resources
* Policies - A document that defines one (or more permissions)

### IAM - Lab
* IAM does not have a region as it is global
Steps to set up IAM on AWS are as follows:
 1. Delete root access keys
 2. Activate MFA on root account
 3. Create individual IAM users
 4. Use groups to assign permissions
 5. Apply an IAM password policy
* IAM roles are a secure way to grant permissions to entities that you trust.

### Create a Billing Alarm - Lab
* We can create a billing alarm by navigating to CloudWatch and configuring alarms for billing

### What Have We Learned?
* IAM consists of the following:
 1. Users
 2. Groups
 3. Roles
 4. Policy Documents
* IAM is universal, it does not apply to regions at this time
* The "root account" is simply the account created on AWS account setup. This account has complete Admin access
* New users have no permissions when first created
* New users are assigned Access Key ID and Secret Access Keys when first created
* Access Key ID & Secret Access Keys are not the same as a password and you cannot use them to login to the console. You can use these keys to access AWS via the APIs and CLI however
* You only get to view the Access Key ID & Secret Access Keys once. If lost will need to be regenerated.
* Always setup MFA (Multifactor Authentication) on the root account
* It is possible to create and customize the password rotation policies

## Section 3 Quiz

**1. Which statement best describes IAM**
* IAM Allows you to manage users, groups, roles, and their corresponding level of access to the AWS platform

**2. Which of the following is NOT a feature of IAM?**
* Allows you to set biometric authentication, so that no passwords are required

**3. Power User Access allows ___**
* Access to all AWS services except for management of groups and users within IAM

**4. What level of access does the "root" account have?**
* Administrator Access

**5. You are a solutions architect working for a large engineering company who are moving their existing legacy hardware to AWS. You have configured their first AWS account and you have set up IAM. Your company will be primarily based out of West Germany, however they will have a small subsidiary operating out of South Korea and you will need an AWS environment configured there as well. Which of the following statements is true;**
* You will need to configure Users and Policy Documents only once, as these are applied globally

**6. You have a client who is considering moving to AWS services and do not yet have an account. What is the first thing the company should do to set up an AWS Account?**
* Set up an account using their company email address

**7. You are a security administrator working for a hotel chain. You have a new member of staff who has started as a systems administrator and they will need full access to the AWS console. You have created the user account and generated the access key id and the secret access key. You have moved this user into the group where the other administrators are and you have provided the new user with their secret access key and their access key id. However when they go to log in to the AWS console, they cannot sign in. What could be the cause of this?**
* You cannot log in to the AWS console using the Access Key ID and Secret Access Key, instead you must generate a password for the user and supply the user with this password, as well as the unique link to sign in to the AWS console

**8. What is an additional way to secure IAM for both the root login and new users alike?**
* Implement MFA for all accounts

**9. By default when you create a new user in the IAM console, what level of access do they have?**
* No access to all AWS services

**10. In what language are policy documents written in?**
* JSON
