# [RDS](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/02-Amazon%20Relational%20Database%20Service(RDS).md) Multi AZ(Disaster Recovery)
- Sync replication.
- One DNS name - automatic app failover to standby.
- Increase availability.
- Failover in case of loss of AZ, loss on network, instance or storage failure.
- No manual intervention in apps.
- Not used for scaling.
- The [Read Replicas](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/03-RDS,%20Aurora%20&%20ElastiCache/01-RDS%20Read%20Replicas.md) be setup as Multi AZ for Disaster Recovery.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202130432.png)


# RDS: From Single-AZ to Multi-AZ
- Zero downtime operation(no need to stop the DB).
- A snapshot is taken.
- A new DB is restored from the snapshot in a new AZ.
- Synchronization is established between the two databases.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241202130716.png)