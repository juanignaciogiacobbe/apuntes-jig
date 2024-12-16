
!!! important Relational Databases
> - **Data is stored in a way that relates it to other pieces of data**.
> - Relational databases use **structured query language (SQL)** to store and query data. **This approach allows data to be stored in an easily understandable, consistent, and scalable way**.

# Amazon Relational Database Service(Amazon RDS)
- **Enables you to run relational databases in the AWS Cloud**.
- Managed DB service for DB use SQL as a query language.
- With these capabilities, **you can spend less time completing administrative tasks and more time using data to innovate your applications**. 

## Amazon RDS database engines
- **Amazon RDS is available on six database engines**, which optimize for memory, performance, or input/output (I/O). Supported database engines include:
	- Amazon Aurora.
	- PostgreSQL.
	- MySQL.
	- MariaDB.
	- Oracle Database.
	- Microsoft SQL Server.


!!! warning RDS VS Deploying DB on [EC2](AWS/Cloud Practitioner (CLF-C02)/02-Compute in the Cloud/01-Amazon Elastic Compute Cloud(EC2).md)
- RDS is a managed service:
	- Automated provisioning, OS patching.
	- Continuous backups and restore to specific timestamp(Point in Time Restore).
	- Monitoring Dashboards.
	- Read replicas for improved read performance.
	- Multi [AZ](AWS/Cloud Practitioner (CLF-C02)/03-Infrastructure and Realiability/02-Availability Zones.md) setup for DR(Disaster Recovery).
	- Maintenance windows for upgrades.
	- Scaling Capabiliy(Vertical and Horizontal).
	- Storage backed by [EBS](AWS/AWS Solutions Architect Associate Certification SAA-C03/02-EC2 Instance Storage/01-EBS.md).
- You can't SSH into your instances.

---

!!! important RDS Storage Auto Scaling
> - Helps you increase storage on your RDS DB instance dynamically.
> - When RDS detects you are running out of free database storage, it scales automatically.
> - Avoid manually scaling your database storage.
> - You have to set the Maximum Storage Threshold(Maximum limit for DB storage).
> - Useful for applications with unpredictable workloads.
> - Supports all RDS database engines.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202125218.png)

