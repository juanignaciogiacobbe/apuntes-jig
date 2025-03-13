
# AWS DataSync
- Move large amount of data to and from:
	- On-premises/ other cloud to AWS(needs agent).
	- AWS to AWS(different storage services).
- Can synchronize to [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|S3]], [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/04-Amazon EFS|EFS]], [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Storage Extras/Amazon FSx|FSx]].
- Replication tasks can be scheduled hourly, daily, weekly.
- File permissions and metadata are preserved.
- One agent task can use 10 Gbps, can setup a bandwidth limit.

!!! note "AWS DataSync"
> - For Data migrations from on-premises to AWS storage services.
> - A DataSync Agent is deployed as a VM and connects to your internal storage.
> - Encryption and Data validation.

![[AWS/AWS Machine Learning Specialty MLS-C01/img/Pasted image 20241204120836.png]]