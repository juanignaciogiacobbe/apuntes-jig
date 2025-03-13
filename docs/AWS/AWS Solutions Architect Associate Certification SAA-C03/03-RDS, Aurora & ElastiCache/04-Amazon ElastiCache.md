# Amazon ElastiCache
- The same way [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/02-Amazon Relational Database Service RDS|RDS]] is to get managed Relational Databases -> ElastiCache is to get managed Redis or Memcached.
- Caches are in-memory databases with really high performance, low latency -> It helps to reduce load off of databases for read intensive workloads, and to make your application stateless.
- AWS takes care of OS maintenance/patching, optimizations, setup, configuration, monitoring, failure recovery and backups.
- **Using ElastiCache involves heavy application code changes.**


## Use Case: DB Cache
- Applications queries ElastiCache, if not available, get from RDS and store in ElastiCache.
- Helps relieve load in RDS.
- Cache must have an invalidation strategy to make sure only the most current data is used in there.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220094146.png]]

---

## Redis VS Memcached

| Redis                                                                                                | Memcached                                                                                            |
| ---------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Multi-AZ Auto-Failover.                                                                              | Multi-Node for partitioning of data(sharding).                                                       |
| Read replicas to scale reads and have high availability.                                             | No high availability(replication).                                                                   |
| Data Durability using AOF persistence.                                                               | Non persistent.                                                                                      |
| Backup and restore features.                                                                         | No backup and restore.                                                                               |
| Supports Sets and Sorted Sets.                                                                       | Multi-threaded architecture.                                                                         |
| ![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220094635.png]] | ![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220094646.png]] |

---

## Cache Security
- ElastiCache supports [[AWS/AWS Cloud Practitioner CLF-C02/06-Security/22- AWS Identity and Access Management IAM|IAM]] authentication for Redis.
- IAM policies on ElastiCache are only used for AWS API-level security.
- Redis AUTH:
	- You can set a "password/token" when you create a Redis cluster.
	- This is an extra level of security for your cache(on top of security groups).
	- Support SSL in flight encryption.
- Memcached:
	- Supports SASL-based authentication(advanced).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241220095013.png]]
