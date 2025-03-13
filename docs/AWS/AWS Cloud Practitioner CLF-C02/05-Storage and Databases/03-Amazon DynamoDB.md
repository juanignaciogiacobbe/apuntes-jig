
!!! note "Nonrelational Databases"
> - Nonrelational databases are sometimes referred to as “NoSQL databases” because they **use structures other than rows and columns to organize data**. One type of structural approach for nonrelational databases is **key-value** pairs. 
> - With key-value pairs, data is organized into items (keys), and items have attributes (values). 
> - In a key-value database, you can add or remove attributes from items in the table at any time.
> - Distributed. It scale horizontally.


# Amazon DynamoDB
- **A key-value database service**(NoSQL database).
- It delivers single-digit millisecond performance at any scale.
- DynamoDB is [[AWS/AWS Cloud Practitioner CLF-C02/02-Compute in the Cloud/04-Serverless Computing|serverless]], which means that **you do not have to provision, patch, or manage servers**. You also do not have to install, maintain, or operate software. -> Low cost and auto-scaling capabilities.
- As the size of your database shrinks or grows, **DynamoDB automatically scales to adjust for changes in capacity while maintaining consistent performance**. This makes it a suitable choice for use cases that require high performance while scaling.
- Chooses Performance over Consistency while delivering reads. During a read, it will look for the nearest & most available storage location for fulfilling the read request.
- Allows event driven programming with DynamoDB Streams.

---

## Read/Write Capacity Modes
- Control how you manage your table's capacity(read/write throughput).

#### Provisioned Mode(default)
- Tables must have provisioned read and write capacity units.
- Option to setup auto-scaling of throughput to meet demand. Throughput can be exceeded temporarily using "Burst Capacity".
- You specify the number of reads/writes per second.
- You need to plan capacity beforehand.
- Pay for provisioned Read Capacity Units(RCU) & Write Capacity Units(WCU).
- Possibility to add auto-scaling mode for RCU & WCU.

#### On-Demand Mode
- Read/writes automatically scale up/down with your workloads.
- No capacity planning needed.
- Pay for what you use, more expensive.
- Great for unpredictable workloads, steep sudden spikes.

---

## DynamoDB Accelerator(DAX)
- Fully-managed, highly available, seamless in-memory cache for DynamoDB.
- Microseconds latency for cached reads & queries.
- Doesn't require application logic modification.
- Up to 10 nodes in the cluster, Multi-AZ, Secure.

![[AWS/AWS Cloud Practitioner CLF-C02/img/Pasted image 20250206160317.png]]
