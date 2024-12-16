
!!! important Amazon Machine Image(AMI)
> - Customization of an [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) instance. -> You add your own software, configuration, OS, monitoring.. -> Faster boot / configuration time because all your software is prepackaged.
> - AMI are built for a specific region(and can be copied across regions).

# AMI Process(from an EC2 instance)
- Start an EC2 instance and customize it.
- Stop the instance(for data integrity).
- Build an AMI - This will also create [EBS](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/01-EBS.md) snapshots.
- Launch instances from other AMIs.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241105091704.png)