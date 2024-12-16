
!!! important Instantiating Applications Quickly
> When launching a full stack([[AWS/Cloud Practitioner (CLF-C02|EC2]]/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md), [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md|EBS]], [[AWS/Cloud Practitioner (CLF-C02|RDS]]/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md)), it can take time to:
> - Install applications.
> - Insert initial(or recovery) data.
> - Configure everything.
> - Launch the application.


!!! warning Tricks
- EC2 Instances:
	- Use a golden [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/02-AMI.md|AMI]]: Install your applications, OS dependencies, etc beforehand and launch your EC2 instance from the Golden AMI.
	- Bootstrap using User Data: For dynamic configuration, use User Data scripts.
	- Hybrid: Mix Golden AMI and User Data([[AWS/AWS Solutions Architect Associate Certification SAA-C03/05-Classic Solutions Architecture/02-Elastic Beanstalk.md|Elastic Beanstalk]]).
- RDS Databases:
	- Restore from a snapshot: The DB will have schemas and data ready.
- EBS Volumes: 
	- Restore from a snapshot: The disk will already be formatted and have data.