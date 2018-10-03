# Section 8: VPC

This section will cover an in-depth overview on AWS VPC.

### What is a VPC?
Think of a VPC (Virtual Private Cloud) as a virtual data centre in the cloud. A VPC lets you provision a logically isolated section of the AWS cloud where you can launch AWS resources in a virtual network that you define. You have complete control over you virtual networking environment, including selection of your own IP address range, creation of subnets, and configuration of route tables and network gateways.

<div align="center">
  <img src="aws-vpc.jpg">
  <h3>Figure 8-1. Diagram of a VPC setup on AWS</h3>
</div>

### What can you do with a VPC?
* Launch instances into a subnet of your choosing
* Assign custom IP address ranges in each subnet
* Configure route tables between subnets
* Create internet gateway and attach it to our VPC
* Much better security control over your AWS resources
* Instance security groups
* Subnet network ACLs (access control lists)

### Default VPC vs Custom VPC
* Default VPC is user friendly, allowing you to immediately deploy instances
* All subnets in default VPC have a route out to the internet
* Each EC2 instance has both a public and private IP address

### Peering VPC
* Allows you to connect one VPC with another via a direct network route using private IP addresses
* Instances behave as if they were on the same private network
*  You can peer VPC's with other AWS accounts as well as with other VPC's in the same account
*  Peering is in a star configuration: i.e. one central VPC peers with 4 others. No transitive peering

### VPC - Exam Tips
* Think of a VPC as a logical datacenter in AWS
* Consists of IGW (Virutal Private Gateways), route tables, network access control lists, subnets, and security groups
* 1 Subnet = 1 AZ
* Security groups are stateful; network access control lists are stateless
* **No transitive peering**

### Exam Tips - Network ACLs
* Your VPC automatically comes with a default network ACL and by default it allows all outbound and inbound traffic
* You can create custom network ACLs. By default each custom network ACL denies all inbound and outbound traffic until you add rules
* Each subnet in your VPC must be associated with a network ACL. If you do not explicitly associate a subnet with a network ACL, the subnet is automatically associated with a network ACL
* You can assoicate a network ACL with multiple subnets; however, a subnet can be associated with only one network ACL at a time. When you associate a network ACL with a subnet, the previous associate is removed
* Network ACLs contain a numbered list of rules that is evaluated in order, starting with the lowest numbered rule
* Network ACLs have separate inbound and outbound rules, and each rule can either allow or deny traffic
* Network ACLs are stateless; responses to allow inbound traffic are subject to the rules for outbound traffic (and vice versa)
* Block IP addresses using network ACLs not security groups
