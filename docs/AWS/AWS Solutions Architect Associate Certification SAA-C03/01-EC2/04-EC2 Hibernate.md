# [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) Hibernate
- We can stop and terminate instances:
	- **Stop**: The data on disk(EBS) is kept intact in the next start.
	- **Terminate**: Any EBS volumes(root) also set-up to be destroyed is lost.
- Introducing EC2 Hibernate:
	- The in-memory(RAM) state is preserved.
	- The instance boot is much faster(The OS is not stopped/restarted).
	- Under the hood: The RAM state is written to a file in the root [EBS](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/01-EBS.md) volume.
- Use cases:
	- Long-running processing.
	- Saving the RAM state.
	- Services that take time to initialize.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241104155713.png)