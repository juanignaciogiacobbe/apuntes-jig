
!!! important Object Storage
> - **Each object consists of data, metadata, and a key**. -> An object’s **key** is its unique identifier.
> - When you modify a file in block storage, only the pieces that are changed are updated. When a file in object storage is modified, the entire object is updated.
> - The **data** might be an image, video, text document, or any other type of file. 
> - **Metadata** contains information about what the data is, how it is used, the object size, and so on. 

![[../img/object_storage.png]]

---

!!! important Amazon Simple Storage Service(S3)
> - It's advertised as a "infinitely scaling" storage.
> - Provides **object-level storage**. -> **S3 stores data as objects in buckets**. 
> - Buckets must have a globally unique name(across all Regions all accounts). -> Are defined at the Region level.
> - It looks like a global service but buckets are created in a Region.
> - Durability: Objects are never lost or compromised.
> - Availability: You can access your data quickly when you need it.
> - You can set permissions to control visibility and access to the uploaded files. 
> - You can also use the Amazon S3 versioning feature to track changes to your objects over time.
> - You can set security at the bucket level or individual object level using access control lists (ACLs), bucket policies, or access point policies.


!!! warning S3 Use Cases
- Backup and Storage.
- Disaster Recovery.
- Archive.
- Hybrid Cloud Storage.
- Application/Media Hosting.
- Data Lakes && Big Data Analytics.
- Software Delivery.
- Static Website.


!!! important Amazon S3 Static Website Hosting
> S3 can host static websites and have them accesible on the [[Redes/Chapter 1/01-Internet.md|Internet]].
> - If you get a 403 Forbidden error, make sure the Bucket Policy allows public reads.


!!! warning S3 Versioning
> You can version your files in Amazon S3. -> It is enabled at the bucket level.
> 
- Same key overwrite will change the "version": 1, 2, 3, ...
 - It is the best practice to version your buckets: 
	 - Protect against unintended deletes(ability to restore a version).
	- Easy roll back to previous version.
- Any file that is not versioned prior to enabling versioning will have version "null".
- Suspending versioning does not delete the previous versions.
![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203101410.png]]

---

!!! important Amazon S3 Replication(CRR & SRR)
- Must enable Versioning in source and destination buckets.
- Cross-Region Replication(CRR). -> Compliance, lower latency access, replication across accounts
- Same-Region Replication(SRR). -> Log aggregation, live replication between production and test accounts.
- Buckets can be in different AWS accounts.
- Copying is asynchronous.
- Must give proper IAM permissions to S3.


!!! warning Replication
- After you enable Replication, only new objects are replicated.
- You can replace existing objects using S3 Batch Replication -> Replicates existing objects and objects that failed replication.
- For `DELETE` operations:
	- Can replicate delete markers from source to target(optional setting).
	- Deletions with a version ID are not replicated(to avoid malicious deletes).
- There is no "chaining" of replication:
	- If bucket I has replication into bucket 2, which has replication into bucket 3.
	- Then objects created in bucket I are not replicated to bucket 3.

## Amazon S3 Storage Classes
- **You only pay for what you use.**
- Can move between classes manually or using S3 Lifecycle configurations.
- When selecting an Amazon S3 storage class, you have to consider these two factors:
	- How often you plan to retrieve your data.
	- How available you need your data to be.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203102402.png]]

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203102428.png]]
### S3 Standard
- Designed for **frequently accessed data**.
- Stores data in a minimum of three Availability Zones.
- Provides **high availability for objects**. This makes it a good choice for a wide range of use cases, such as websites, content distribution, and data analytics. 
- Amazon S3 Standard has a higher cost than other storage classes intended for infrequently accessed data and archival storage.

### S3 Standard-Infrequent Access(S3 Standard-IA)
- Ideal for **infrequently accessed data**.
- Similar to Amazon S3 Standard but has a lower storage price and higher retrieval price.
- **Ideal for data infrequently accessed but requires high availability when needed**. Both Amazon S3 Standard and Amazon S3 Standard-IA store data in a minimum of three Availability Zones. Amazon S3 Standard-IA provides the same level of availability as Amazon S3 Standard but with a lower storage price and a higher retrieval price.}

## S3 One Zone-Infrequent Access(S3 One Zone-IA)
- **Stores data in a single Availability Zone**.
- **Has a lower storage price than Amazon S3 Standard-IA**.
- This makes it a good storage class to consider if the following conditions apply:
	- You want to save costs on storage.
	- You can easily reproduce your data in the event of an Availability Zone failure.


## S3 Intelligent-Tiering
- Ideal for **data with unknown or changing access patterns**.
- **Requires a small monthly monitoring and automation fee per object**.
- Amazon S3 monitors objects’ access patterns.
- If you haven’t accessed an object for 30 consecutive days, Amazon S3 automatically moves it to the infrequent access tier, S3 Standard-IA. If you access an object in the infrequent access tier, Amazon S3 automatically moves it to the frequent access tier, S3 Standard.

## S3 Glacier Instant Retrieval
- Works well for **archived data that requires immediate access**.
- **Can retrieve objects within a few milliseconds**.
- You can retrieve objects stored in the S3 Glacier Instant Retrieval storage class within milliseconds, with the same performance as S3 Standard.

## S3 Glacier Flexible Retrieval
- **Low-cost storage designed for data archiving**.
- **Able to retrieve objects within a few minutes to hours**.
- For example, you might use this storage class to store archived customer records or older photos and video files. You can retrieve your data from S3 Glacier Flexible Retrieval from 1 minute to 12 hours.

## S3 Glacier Deep Archive
- **Lowest-cost object storage class ideal for archiving**.
- **Able to retrieve objects within 12 hours**.
- S3 Deep Archive supports long-term retention and digital preservation for data that might be accessed once or twice in a year.
- All objects from this storage class are replicated and stored across at least three geographically dispersed Availability Zones.

## S3 Outposts
- Creates S3 buckets on Amazon S3 Outposts.
- Makes it easier to retrieve, store, and access data on AWS Outposts.
- Amazon S3 Outposts delivers object storage to your on-premises AWS Outposts environment.
- Designed to store data durably and redundantly across multiple devices and servers on your Outposts.