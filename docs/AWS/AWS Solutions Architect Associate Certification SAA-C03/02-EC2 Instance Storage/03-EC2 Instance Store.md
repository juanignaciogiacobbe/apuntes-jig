
!!! important EC2 Instance Store
> - [EBS](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/01-EBS.md) volumes are network drives with good but "limited" performance. -> If you need high-performance hardware disk, use [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) Instance Store.
> - It gives us better I/O performance.
> - EC2 Instance Store lose their storage if they're stopped(ephemeral).
> - Good for buffer, cache, scratch data, temporary content.
> - Risk of data loss if hardware fails. -> Backups and Replication are your responsibility.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202101755.png)