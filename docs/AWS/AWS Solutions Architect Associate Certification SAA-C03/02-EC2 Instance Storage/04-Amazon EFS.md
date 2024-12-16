
!!! important File Storage
> - **Multiple clients can access data that is stored in shared file folders**.
> - A storage server uses block storage with a local file system to organize files. Clients access data through file paths.
> - File storage is **ideal for use cases in which a large number of services and resources need to access the same data at the same time**.

!!! important Elastic File System(EFS)
> - Managed NFS(network file system) that can be mounted on many [EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md).
> - Works with EC2 instances in Multi-[AZ](AWS/Cloud Practitioner (CLF-C02)/03-Infrastructure and Realiability/02-Availability Zones.md).
> - Highly available, scalable, expensive, pay per use.
> - Uses NFSv4.1 protocol.
> - Uses security group to control access to EFS.
> - Compatible with Linux based [AMI](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI.md)(Not Windows).
> - Encryption at rest using KMS.
> - Use cases: Content management, web serving, data sharing, Wordpress.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241105095901.png)

> [!PDF|yellow] [AWS Certified Solutions Architect Slides v39, p.114](AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=114&selection=8,0,12,29&color=yellow)
> > EFS – Performance & Storage Classes
> 
> 
