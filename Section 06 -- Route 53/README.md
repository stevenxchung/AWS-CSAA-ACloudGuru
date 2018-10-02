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
* Top level domain names are controlled bvy the IANA (Internet Assigned Numbers Authority) in a root zone database which is essentially a database of all available top level domains

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
* The address record is used by a computer to tranlate the name of the domain to an IP address

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
