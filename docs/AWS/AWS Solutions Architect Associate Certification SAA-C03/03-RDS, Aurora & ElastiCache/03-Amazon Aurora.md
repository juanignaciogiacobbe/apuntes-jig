# Amazon Aurora
- **Helps to reduce your database costs by reducing unnecessary input/output (I/O) operations,** while ensuring that your database resources remain reliable and available.
- **Consider Amazon Aurora if your workloads require high availability**. It replicates six copies of your data across three Availability Zones and continuously backs up your data to [01-Amazon Simple Storage Service(S3)](AWS/Cloud Practitioner (CLF-C02)/05-Storage and Databases/01-Amazon Simple Storage Service(S3).md).


!!! important Amazon Aurora
> - It is compatible with MySQL and PostgreSQL relational databases. 
> - **Up to 5x faster than standard MySQL databases and up to three times faster than standard PostgreSQL databases**.
> - Failover is instantaneous -> It's High Availability native.

> [!PDF|yellow] [AWS Certified Solutions Architect Slides v39, p.171](AWS/Slides/AWS Certified Solutions Architect Slides v39.pdf#page=171&selection=8,0,8,41&color=yellow)
> > Aurora High Availability and Read Scaling

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202131417.png)


!!! note Features of Aurora
- Automatic Failover.
- Backup and Recovery.
- Isolation and Security.
- Industry Compliance.
- Push-Button scaling.
- Automated Patching with Zero Downtime.
- Advanced Monitoring.
- Routine Maintenance.
- Backtrack: Restore data at any point of time without using backups.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202131825.png)


!!! important Aurora Custom Endpoints
> - Define a subset of Aurora Instances as a Custom Endpoint.
> - The Reader Endpoint is generally not used after defining Custom Endpoints.

---

!!! important Aurora Serverless
> - Automated database instantiation and autoscaling based on actual usage.
> - Good for infrequent,intermittent of unpredictable workloads.
> - No capacity planning needed.
> - Pay per second, can be more cost-effective.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202132125.png)