
!!! important Amazon Machine Image(AMI)
> - Customization of an [[AWS/Cloud Practitioner (CLF-C02|EC2]]/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md) instance. -> You add your own software, configuration, OS, monitoring.. -> Faster boot / configuration time because all your software is prepackaged.
> - AMI are built for a specific region(and can be copied across regions).

# AMI Process(from an EC2 instance)
- Start an EC2 instance and customize it.
- Stop the instance(for data integrity).
- Build an AMI - This will also create [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md|EBS]] snapshots.
- Launch instances from other AMIs.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241105091704.png]]