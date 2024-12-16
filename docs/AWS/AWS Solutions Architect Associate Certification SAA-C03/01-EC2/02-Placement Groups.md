# Placement Groups
- It lets you define your [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) instance placement strategy.
- When you create a placement group, you specify one of the following strategies for the group:
	- **Cluster**: Clusters instances into a low-latency group in a single [Availability Zone](AWS/Cloud%20Practitioner%20(CLF-C02)/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md).
		![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241104152537.png)
		- It enhances networking. -> Great performance for any kind of computational job.
		- If the AZ fails, all instances fails at the same time.
		- Use case: Big Data job that needs to complete fast. Applications that needs extremely low latency and high network throughput.
	- **Spread**: Spreads instances across underlying hardware(max 7 instances per group per AZ).
		![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241104152834.png)
		- The can span across Availability Zones(AZs).
		- Reduced risk of simultaneous failure.
		- EC2 instances are on different physical hardware.
		- Use case: Application that needs to maximize high availability. Critical applications where each instance must be isolated from failure from each other.
	- **Partition**: Spreads instances across many different partitions(which rely on different sets of racks) within an AZ. Scales to 100s of EC2 instances per group.
		![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241104153127.png)
		- Up to 7 partitions per AZ.
		- Can span across multiple AZs in the same region.
		- The instances in a partition do not share racks with the instances in the other partitions.
		- A partition failure can affect many EC2 but won't affect other partitions.
		- EC2 instances get access to the partition information as metadata.