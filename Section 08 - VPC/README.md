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
* Subnet network ACLS (access control lists)

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
