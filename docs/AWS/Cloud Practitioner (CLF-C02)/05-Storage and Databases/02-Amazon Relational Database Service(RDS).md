
> [!IMPORTANT] Relational Databases
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


> [!WARNING] RDS VS Deploying DB on [EC2](AWS/Cloud%20Practitioner%20(CLF-C02)/02-Compute%20in%20the%20Cloud/01-Amazon%20Elastic%20Compute%20Cloud(EC2).md)
- RDS is a managed service:
	- Automated provisioning, OS patching.
	- Continuous backups and restore to specific timestamp(Point in Time Restore).
	- Monitoring Dashboards.
	- Read replicas for improved read performance.
	- Multi [AZ](AWS/Cloud%20Practitioner%20(CLF-C02)/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md) setup for DR(Disaster Recovery).
	- Maintenance windows for upgrades.
	- Scaling Capabiliy(Vertical and Horizontal).
	- Storage backed by [EBS](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/02-EC2%20Instance%20Storage/01-EBS.md).
- You can't SSH into your instances.

---

> [!IMPORTANT] RDS Storage Auto Scaling
> - Helps you increase storage on your RDS DB instance dynamically.
> - When RDS detects you are running out of free database storage, it scales automatically.
> - Avoid manually scaling your database storage.
> - You have to set the Maximum Storage Threshold(Maximum limit for DB storage).
> - Useful for applications with unpredictable workloads.
> - Supports all RDS database engines.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202125218.png)

