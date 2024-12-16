# [[AWS/Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] Hibernate
- We can stop and terminate instances:
	- **Stop**: The data on disk(EBS) is kept intact in the next start.
	- **Terminate**: Any EBS volumes(root) also set-up to be destroyed is lost.
- Introducing EC2 Hibernate:
	- The in-memory(RAM) state is preserved.
	- The instance boot is much faster(The OS is not stopped/restarted).
	- Under the hood: The RAM state is written to a file in the root [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]] volume.
- Use cases:
	- Long-running processing.
	- Saving the RAM state.
	- Services that take time to initialize.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241104155713.png]]