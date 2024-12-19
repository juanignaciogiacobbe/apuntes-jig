# Amazon Machine Image(AMI)

!!! note "Amazon Machine Image(AMI)"
> - Customization of an [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]] instance. -> You add your own software, configuration, OS, monitoring... -> Faster boot / configuration time because all your software is prepackaged.
> - AMI are built for a specific region(and can be copied across regions).

# AMI Process(from an EC2 instance)
- Start an EC2 instance and customize it.
- Stop the instance(for data integrity).
- Build an AMI - This will also create [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS|EBS]] snapshots.
- Launch instances from other AMIs.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241105091704.png]]