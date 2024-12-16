# [[AWS/Cloud Practitioner (CLF-C02|EC2]]/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) Hibernate
- We can stop and terminate instances:
	- **Stop**: The data on disk(EBS) is kept intact in the next start.
	- **Terminate**: Any EBS volumes(root) also set-up to be destroyed is lost.
- Introducing EC2 Hibernate:
	- The in-memory(RAM) state is preserved.
	- The instance boot is much faster(The OS is not stopped/restarted).
	- Under the hood: The RAM state is written to a file in the root [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md|EBS]] volume.
- Use cases:
	- Long-running processing.
	- Saving the RAM state.
	- Services that take time to initialize.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241104155713.png]]