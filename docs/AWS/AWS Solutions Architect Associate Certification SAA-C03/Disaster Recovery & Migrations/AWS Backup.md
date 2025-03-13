# AWS Backup
- Fully managed service. -> Centrally manage and automate backups across AWS services.
- No need to create custom scripts and manual processes.
- Supported services: [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud EC2|EC2]], [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|S3]], [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/02-Amazon Relational Database Service RDS|RDS]], DocumentDB, [[AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/04-Amazon EFS|EFS]], [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Storage Extras/Amazon FSx|FSx]], [[AWS/AWS Solutions Architect Associate Certification SAA-C03/Storage Extras/AWS Storage Gateway|Storage Gateway]].
- Supports cross-region backups, and cross-account backups.
- On-Demand and Scheduled backups.
- Tag-based backup policies.
- You create backups policies known as Backup Plans:
	- Backup frequency.
	- Backup window.
	- Transition to Cold Storage.
	- Retention Period.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250116091930.png]]


---


## AWS Backup Vault Lock
- Enforce a WORM(Write Once Read Many) state for all the backups that you store in your AWS Backup Vault.
- Additional layer of defense to protect your backups against:
	- Inadvertent or malicious delete operations.
	- Updates that shorten or alter retention periods.
- Even the root user cannot delete backups when enabled.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250116092112.png]]
