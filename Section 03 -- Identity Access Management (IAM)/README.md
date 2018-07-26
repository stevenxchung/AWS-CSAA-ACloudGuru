# Section 3: Identity Access Management (IAM)

This section will cover an in-depth overview on the IAM service.

### IAM Overview
* Centralised control of your AWS account
* Shared Access to your AWS account
* Identity Federation (including Active Directory, Facebook, LinkedIn, etc)
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
