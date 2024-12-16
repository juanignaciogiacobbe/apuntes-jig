# [RDS](AWS/Cloud Practitioner (CLF-C02)/05-Storage and Databases/02-Amazon Relational Database Service(RDS).md) Multi AZ(Disaster Recovery)
- Sync replication.
- One DNS name - automatic app failover to standby.
- Increase availability.
- Failover in case of loss of AZ, loss on network, instance or storage failure.
- No manual intervention in apps.
- Not used for scaling.
- The [Read Replicas](AWS/AWS Solutions Architect Associate Certification SAA-C03/03-RDS, Aurora & ElastiCache/01-RDS Read Replicas.md) be setup as Multi AZ for Disaster Recovery.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202130432.png)


# RDS: From Single-AZ to Multi-AZ
- Zero downtime operation(no need to stop the DB).
- A snapshot is taken.
- A new DB is restored from the snapshot in a new AZ.
- Synchronization is established between the two databases.

![](AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241202130716.png)