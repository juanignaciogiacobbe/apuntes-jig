# [RDS](AWS/Cloud Practitioner (CLF-C02)/05-Storage and Databases/02-Amazon Relational Database Service(RDS).md) Read Replicas
- Up to 15 Read Replicas within [AZ](AWS/Cloud Practitioner (CLF-C02)/03-Infrastructure and Realiability/02-Availability Zones.md), Cross AZ or Cross Region.
- Replication is Async, so reads are eventually consistent.
- Replicas can be promoted to their own DB.
- Applications must update the connection string to leverage read replicas.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202125553.png)


!!! warning Read Replicas: Use Cases
- You have a production database that is taking on normal load.
- You want to run a reporting application to run some analytics.
- You create a Read Replica to run the new workload there.
- The production application is unaffected.
- Read Replicas are used for `SELECT`(=read) only kind of statements(not `INSERT`, `UPDATE`, `DELETE`).

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202125823.png)


!!! warning Network Cost
- There's a network cost when data goes from one AZ to another.
- For RDS Read Replicas within the same Region, you don't pay that fee.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202125959.png)