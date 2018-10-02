# Section 6: Route 53

This section will cover an in-depth overview on the AWS Route 53 service.

### What is DNS?
DNS is used to convert human friendly domain names into an IP (Internet Protocol) address.
* IP addresses are used by computers to identify each other on the network
* IP addresses commonly come in 2 different forms, IPv4 and IPv6

### IPv4 vs IPv6
* IPv4 space is a 32 bit field has over 4 billion (4,294,967,296) different addresses
* IPv6 had an address space of 128 bits which is 340 undecillion addresses

### Top Level Domains
* The last word in a domain name represents the top level domain name (i.e. the .com in google.com) whereas the second word in a domain name is known as the second level domain name (i.e. acloud.guru)
* Top level domain names are controlled by the IANA (Internet Assigned Numbers Authority) in a root zone database which is essentially a database of all available top level domains

### Domain Registrars
* A registrar is an authority that can assign domain names directly under one or more top-level domains. Each domain name becomes registered in a central database known as the WhoIS database.

### SOA (Start of Authority) Record
* The SOA records stores information about:
  * The name of the server that supplied that data for the zone
  * The administrator of the zone
  * The current version of the data file
  * The default number of seconds for the time-to-live file on resource records

### NS Records
* NS (Name Server) records are used by top level domain servers to direct traffic to the content DNS server which contains the authoritative DNS records

### A Records
* The address record is used by a computer to translate the name of the domain to an IP address

### TTL
* The length that a DNS record is cached on either the resolving server or the users own local PC is to the value of the TTL (Time To Live) in seconds.

### CNames
* A CName (Canonical Name) can be used to resolve one domain name to another

### Alias Records
* Alias records are used to map resource record sets in your hosted zone to Elastic Load Balancers, CloudFront distributions, or S3 buckets that are configured as websites
* Unlike a CName, an alias record can't be used for naked domain names (zone apex record). It must be either an A record or an alias.

### DNS 101 Exam Tips
* ELBS do not have pre-defined IPv4 addresses; you resolve to them using a DNS name
* Alias record vs CName
* Always choose alias record over a CName

### Common DNS Types
* SOA records
* NS records
* A records
* CNames
* MX records
* PTR records

### Routing Policies Available on AWS
There are several different routing policies on AWS
* Simple routing
* Weighted routing
* Latency-based routing
* Failover routing
* Geolocation routing
* Multivalue answer routing

### Simple Routing Policy - Lab
If you choose simple routing policy you can only have one record with multiple IP addresses. If you specify multiple values in a record, Route 53 returns all values to the user in a random order.

### Weighted Routing Policy - Lab
Weighted routing policies let you split your traffic based on different weights assigned (e.g. you can set 20% of your traffic to go to US-EAST-1 and then 80% to go to EU-WEST-1).

### Latency Routing Policy - Lab
Latency based routing allows you to route you traffic based on the lowest network latency for you end user (i.e. which region will give them the fastest response time). To use latency-based routing, you create a latency resource record set for the EC2 (or ELB) resource in each region that hosts your website. When Route 53 receives a query for your site, it selects the latency resource record set for the region that gives the user the lowest latency. Route 53 then responds with the value associated with that resource record set.

### Failover Routing Policy - Lab
Failover routing policies are used when you want to create an active/passive set up. For example, you may want your primary site to be in EU-WEST-2 and your secondary DR site in AP-SOUTHEAST-2.
* Route 53 will monitor the health or your primary site using a health check
* A health check monitors the health of your end points

### Geolocation Routing Policy - Lab
Geolocation routing lets you choose where your traffic will be sent based on the geographic location of your users.

### Multivalue Routing
If you want to route traffic approximately randomly to multiple resources, such as web servers, you can create one multivalue answer record for each resource and, optionally, associate a Route 53 health check with each record. If you create a dozen multivalue answer records, Route 53 responds to DNS queries with up to eight healthy records in response to each DNS query.

### DNS Exam Tips
Make sure to go over the sections above (mainly routing policy sections) before taking the exam.

## Section 6 Quiz

**1. Does Route 53 support MX Records?**
* Yes

**2. Route 53 is named so because**
* The DNS Port is on Port 53 and Route 53 is a DNS Service

**3. Route 53 does not support zone apex records (or naked domain names)**
* Incorrect

**4. Route53 is Amazon's DNS Service**
* True

**5. There is a limit to the number of domain names that you can manage using Route 53.**
* True and False. There is a limit of domain names, however this limit can be raised by contacting AWS support.
