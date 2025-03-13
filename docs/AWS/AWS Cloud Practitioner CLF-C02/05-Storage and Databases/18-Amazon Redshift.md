# Amazon Redshift
- Fully managed, petabyte-scale **Data warehousing service** that you can use for big data analytics.
- 10X better performance than other DWs. Cost-effective.
- It offers the ability to **collect data from many sources and helps you to understand relationships and trends across your data**.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250206161004.png]]

## Use-Cases
- Accelerate analytics workloads.
- Unified data warehouse & data lake.
- Data warehouse modernization.
- Analyze global sales data.
- Store historical stock trade data.
- Analyze ad impressions & clicks.
- Aggregate gaming data.
- Analyze social trends.

---

## Redshift Spectrum
- Query exabytes of unstructured data in [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|S3]] without loading.
- Limitless concurrency.
- Horizontal scaling.
- Separate storage & compute resources.
- Wide variety of data formats.
- Support of Gzip and Snappy compression.

---

## Redshift Performance
- Massively Parallel Processing(MPP).
- Columnar Data Storage.
- Column Compression.

---

## Redshift Durability
- Replication within cluster.
- Backup to S3 -> Asynchronously replicated to another region.
- Automated snapshots.
- Failed drives/ nodes automatically replaced.
- Limited to a single AZ.
