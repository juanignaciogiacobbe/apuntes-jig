# EC2 Instance Store
- An _instance store_ provides temporary block-level storage for your EC2 instance. This storage is provided by disks that are physically attached to the host computer. Instance store is ideal for temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content. It can also be used to store temporary data that you replicate across a fleet of instances, such as a load-balanced pool of web servers.
- An instance store consists of one or more instance store volumes exposed as block devices. The size of an instance store as well as the number of devices available varies by instance type and instance size. For example, not every instance type provides instance store volumes. 

!!! note "EC2 Instance Store"
> - [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]] volumes are network drives with good but "limited" performance. -> If you need high-performance hardware disk, use [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] Instance Store.
> - It gives us better I/O performance.
> - EC2 Instance Store lose their storage if they're stopped(ephemeral).
> - Good for buffer, cache, scratch data, temporary content.
> - Risk of data loss if hardware fails. -> Backups and Replication are your responsibility.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202101755.png]]