# Storage

## Simple Storage Service (S3)
- S3 is an object storage service that offers scalability, data availability, security, and performance.
- S3 objects are stored in S3 Buckets.
- You can use S3 irrespective of the size of application or organization as AWS charges you only for the data stored, retreival on S3.
- Using KMS or using S3 default encryption, You can also encrypt data stored in S3.
- 99.999999999% (11-9's) durability of objects across multiple AZs.
- Can be used to host static websites without need to provision servers.
- Different versions of a single object by enabling S3 versioning.
- You can use bucket policy, ACLs, to define who and how can the object in S3 Bucket can be accessed. Bucket Policy is a resource based Policy.
- You can choose preferred region of choice for data storage to optimize latency, minimize costs, or address regulatory requirements
- Cross-Region Replication can be used to replicate data between distant AWS Regions.
- S3 Offers Different Storage Classes:

	**a. S3 Standard**
	- Offers high durability, availability, and performance object storage for frequently accessed data.
	- It delivers low latency and high throughput.
	- 99.99% (4-9's) availability annually.

	**b. S3 Intelligent-Tiering**
	- Automatically reduces storage costs by moving data to the most cost-effective access tier based on access frequency, without performance impact, retrieval fees, or operational overhead.
	- can save up to 40% on storage costs (for IA tier) and saves upto 68% (for Archive IA tier)
	- 99.999999999% (11-9's) durability of objects across multiple AZs
	- 99.9% (3-9's) availability annually.
	- Objects smaller than 128KB can be stored in this storage tier

	**c. S3 Standard-IA (Infrequent Access)**
	-  Used for less frequently accessed data, but requires rapid access when needed.
	-  99.9% availability over a given year.

	**d. S3 One Zone-IA**
	- Similar to S3 Standard-IA but stores data in only one AZ instead of 3 AZs thereby saving the cost.
	- Used for data that is non-critical and infrequently accesses.
	- good choice for storing secondary backup copies of on-premises data or easily re-creatable data.
	- 99.5% availability over a given year
	- data stored in this storage class will be lost in the event of Availability Zone destruction.

	**e. Amazon S3 Glacier Instant Retrieval**
	- It is an archive storage class that delivers the lowest-cost storage for long-lived data that is rarely accessed and requires retrieval in milliseconds.
	- 128 KB minimum object size
	- 99.9% data availability in a given year
	- used for data that may or maynot be required in the future such as secondary backups.

	**f. Amazon S3 Glacier Flexible Retrieval (Formerly S3 Glacier)**
	- Similar to `S3 Glacier Instant Retrieval` but is 10% more cheaper.
	- used for storing archive data that is accessed 1-2 times per year and is retrieved asynchronously such as backups.

	**g. Amazon S3 Glacier Deep Archive**
	- Amazon S3’s lowest-cost storage class and supports long-term retention and digital preservation for data that may be accessed once or twice in a year.
	- used to store data that for highly-regulated industries, such as financial services, healthcare, and public sectors - that retain data sets for 7 - 10 years or longer to meet regulatory compliance requirements.
	- Retrieval time is within 12 hours

	**h. S3 Outposts**
	- Delivers object storage to your on-premises AWS Outposts environment.
	- Designed to durably and redundantly store data on your Outposts

## Elastic File System (EFS)
- EFS automatically grows and shrinks as you add and remove files with no need for management or provisioning.
- Unlike EBS Volumes, You can attach EFS to multiple EC2 instances, ECS or Lambdas thereby behaving like a Network File System.
- You can choose from two performance modes and two throughput modes.
- EFS provides both encryption in transit and encryption at rest.
- EFS Storage Classes:

	**1. Standard storage classes:**
	- EFS Standard 
	- EFS Standard–Infrequent Access

	**2. One Zone storage classes**
	- EFS One Zone
	- EFS One Zone–Infrequent Access 

## Labs
### Host Static Website from S3 and Distribute the content using CloudFront CDN
- Create a bucket named as `static.krishnachalise.com.np`
- Create a html page that shows `Welcome to AWS Training` and host it as a static site using S3 for domain s3-`static.krishnachalise.com.np`

### S3 Permissions management using IAM and Bucket Policy
1. Create a IAM User named `s3-user`. Do not attach any permissions to that user. Enable both AWS Management console and programatic Access.
2. Create a bucket named `test-bucket-97850`.
3. Setup AWS-CLI in your laptop with profile `training-profile` and hit the following command in your terminal/PowerShell.
 ```
 aws s3 --profile training-profile ls
```
4. What was the output of the command. Did you get some error? If you got some error. Fix the error by granting required permission to that user and try the above command again.
5. Now login to the AWS Management Console using `s3-user` and upload the test image to that S3.
**Link to Image:** 
https://upload.wikimedia.org/wikipedia/commons/f/ff/Pizigani_1367_Chart_10MB.jpg
6. Were you able to upload the image to S3 bucket. Did you get some error? If you got some error, fix the error by granting the required permission and try uploading again.
7. Now find the Link to the image that was stored in step 6 and browse that URL from another browser or from Incognito.
8. Were you able to open the image or did you get some error? If you got some error, fix the issue by setting up appropriate bucket policy. What was the latency of retreived 
9. Create a cloudfront distribution with name`aws-training-cdn` and `test-bucket-97850` as origin.
10. Now request the object (image) uploaded earlier through CDN, did you experience any difference?
11. Now, Delete the existing bucket policy from bucket `test-bucket-97850`. and again try to request the image. What changes do you see?
12. Add S3 lifecycle policy to `test-bucket-97850` to delete objects older than 1 days

## Reading List
- [AWSDocs - S3 Storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [AWSDocs - S3 Storage Classes ](https://aws.amazon.com/s3/storage-classes/)
- [AWSDocs - S3 Replication](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication.html)
- [AWSDocs - What is EFS?](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)