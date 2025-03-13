# Amazon Elastic File System(EFS)

!!! note "File Storage"
> - **Multiple clients can access data that is stored in shared file folders**.
> - A storage server uses block storage with a local file system to organize files. Clients access data through file paths.
> - File storage is **ideal for use cases in which a large number of services and resources need to access the same data at the same time**.

!!! note "Elastic File System(EFS)"
> - Managed NFS(network file system) that can be mounted on many [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]].
> - Works with EC2 instances in Multi-[[AWS/AWS Cloud Practitioner CLF-C02/03-Infrastructure and Realiability/02-Availability Zones|AZ]].
> - Highly available, scalable, expensive, pay per use.
> - Uses NFSv4.1 protocol.
> - Uses security group to control access to EFS.
> - Compatible with Linux based [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI|AMI]](Not Windows).
> - Encryption at rest using KMS.
> - Use cases: Content management, web serving, data sharing, Wordpress.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241105095901.png]]


---

!!! note "EFS Performance Classes"

- EFS Scale
	- 1000s of concurrent NFS clients, 10GB+ /s throughput.
	- Grow to Petabyte-scale network file system, automatically.
- Performance Mode(set as EFS creation time)
	- General Purpose(default) -> Latency-sensitive use cases(example: ).
	- Max I/O -> Higher latency, throughput, highly parallel(big data, media processing).
- Throughput mode
	- Bursing -> 1TB = 50MiB/s + burst up to 100MiB/s.
	- Provisioned -> Set your throughput regardless of storage size.
	- Elastic -> Automatically scales throughput up or down based on your workloads.



!!! note "EFS Storage Classes"

- Storage Tiers(lifecycle management feature -> Move file after N days).
	- Standard: for frequently accessed files.
	- Infrequent access(EFS-IA): Cost to retrieve files, lower price to store.
	- Archive: Rarely accessed data(few times each year), 50% cheaper.
	- Implement lifecycle policies to move files between storage tiers.
- Availability and Durability
	- Standard: Multi-AZ, great for prod.
	- One zone: One AZ, great for dev, backup enabled by default, compatible with IA(EFS One Zone-IA).
- Over 90% in cost savings.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220090724.png]]
