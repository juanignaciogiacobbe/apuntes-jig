
!!! important Instantiating Applications Quickly
> When launching a full stack([EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md), [EBS](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md), [RDS](AWS/Cloud Practitioner (CLF-C02)/05-Storage and Databases/02-Amazon Relational Database Service(RDS).md)), it can take time to:
> - Install applications.
> - Insert initial(or recovery) data.
> - Configure everything.
> - Launch the application.


!!! warning Tricks
- EC2 Instances:
	- Use a golden [AMI](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI.md): Install your applications, OS dependencies, etc beforehand and launch your EC2 instance from the Golden AMI.
	- Bootstrap using User Data: For dynamic configuration, use User Data scripts.
	- Hybrid: Mix Golden AMI and User Data([Elastic Beanstalk](AWS/AWS Solutions Architect Associate Certification SAA-C03/05-Classic Solutions Architecture/02-Elastic Beanstalk.md)).
- RDS Databases:
	- Restore from a snapshot: The DB will have schemas and data ready.
- EBS Volumes: 
	- Restore from a snapshot: The disk will already be formatted and have data.