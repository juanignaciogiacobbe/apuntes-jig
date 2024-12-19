
!!! note "EC2 Instance Store"
> - [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]] volumes are network drives with good but "limited" performance. -> If you need high-performance hardware disk, use [[01-Amazon Elastic Compute Cloud EC2|EC2]] Instance Store.
> - It gives us better I/O performance.
> - EC2 Instance Store lose their storage if they're stopped(ephemeral).
> - Good for buffer, cache, scratch data, temporary content.
> - Risk of data loss if hardware fails. -> Backups and Replication are your responsibility.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202101755.png]]