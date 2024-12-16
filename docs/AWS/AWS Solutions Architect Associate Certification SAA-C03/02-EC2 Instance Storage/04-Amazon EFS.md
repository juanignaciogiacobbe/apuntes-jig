
> [!IMPORTANT] File Storage
> - **Multiple clients can access data that is stored in shared file folders**.
> - A storage server uses block storage with a local file system to organize files. Clients access data through file paths.
> - File storage is **ideal for use cases in which a large number of services and resources need to access the same data at the same time**.

> [!IMPORTANT] Elastic File System(EFS)
> - Managed NFS(network file system) that can be mounted on many [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md).
> - Works with EC2 instances in Multi-[AZ](AWS/Cloud%20Practitioner%20(CLF-C02)/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md).
> - Highly available, scalable, expensive, pay per use.
> - Uses NFSv4.1 protocol.
> - Uses security group to control access to EFS.
> - Compatible with Linux based [AMI](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/02-AMI.md)(Not Windows).
> - Encryption at rest using KMS.
> - Use cases: Content management, web serving, data sharing, Wordpress.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241105095901.png)

> [!PDF|yellow] [AWS Certified Solutions Architect Slides v39, p.114](AWS/Slides/AWS%20Certified%20Solutions%20Architect%20Slides%20v39.pdf#page=114&selection=8,0,12,29&color=yellow)
> > EFS – Performance & Storage Classes
> 
> 
