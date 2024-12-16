
> [!IMPORTANT] Instantiating Applications Quickly
> When launching a full stack([EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md), [EBS](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/01-EBS.md), [RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md)), it can take time to:
> - Install applications.
> - Insert initial(or recovery) data.
> - Configure everything.
> - Launch the application.


> [!WARNING] Tricks
- EC2 Instances:
	- Use a golden [AMI](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/02-AMI.md): Install your applications, OS dependencies, etc beforehand and launch your EC2 instance from the Golden AMI.
	- Bootstrap using User Data: For dynamic configuration, use User Data scripts.
	- Hybrid: Mix Golden AMI and User Data([Elastic Beanstalk](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/05-Classic%20Solutions%20Architecture/02-Elastic%20Beanstalk.md)).
- RDS Databases:
	- Restore from a snapshot: The DB will have schemas and data ready.
- EBS Volumes: 
	- Restore from a snapshot: The disk will already be formatted and have data.