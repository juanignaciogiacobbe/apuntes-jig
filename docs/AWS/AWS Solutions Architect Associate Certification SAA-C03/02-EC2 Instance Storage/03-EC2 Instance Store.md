
!!! important EC2 Instance Store
> - [EBS](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md) volumes are network drives with good but "limited" performance. -> If you need high-performance hardware disk, use [EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md) Instance Store.
> - It gives us better I/O performance.
> - EC2 Instance Store lose their storage if they're stopped(ephemeral).
> - Good for buffer, cache, scratch data, temporary content.
> - Risk of data loss if hardware fails. -> Backups and Replication are your responsibility.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202101755.png)