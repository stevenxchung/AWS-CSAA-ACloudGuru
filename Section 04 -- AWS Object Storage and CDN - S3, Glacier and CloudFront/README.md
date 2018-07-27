# Section 4: S3

This section will cover an in-depth overview on the S3 service.

### What is S3?
* S3 provides developers and IT teams with secure, durable, highly-scalable object storage. Amazon S3 is easy to use, with a simple web services interface to store and retrieve any amount of data from anywhere on the web
* S3 is a safe place to store your files
* S3 is an object-based storage
* The data is spread across multiple devices and facilities

### The basics
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
 * Metadata (Data about data your are storing)
 * Subresources:
  * Access Control Lists
  * Torrent
