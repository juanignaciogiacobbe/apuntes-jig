# [RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md) Read Replicas
- Up to 15 Read Replicas within [AZ](AWS/Cloud%20Practitioner%20(CLF-C02)/03-Infrastructure%20and%20Realiability/02-Availability%20Zones.md), Cross AZ or Cross Region.
- Replication is Async, so reads are eventually consistent.
- Replicas can be promoted to their own DB.
- Applications must update the connection string to leverage read replicas.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202125553.png)


> [!WARNING] Read Replicas: Use Cases
- You have a production database that is taking on normal load.
- You want to run a reporting application to run some analytics.
- You create a Read Replica to run the new workload there.
- The production application is unaffected.
- Read Replicas are used for `SELECT`(=read) only kind of statements(not `INSERT`, `UPDATE`, `DELETE`).

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202125823.png)


> [!WARNING] Network Cost
- There's a network cost when data goes from one AZ to another.
- For RDS Read Replicas within the same Region, you don't pay that fee.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202125959.png)