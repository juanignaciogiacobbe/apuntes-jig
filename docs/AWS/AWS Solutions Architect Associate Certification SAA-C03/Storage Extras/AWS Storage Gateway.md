# AWS Storage Gateway
- Bridge between on-premises data and cloud data.
- Use cases:
	- Disaster recovery.
	- Backup & restore.
	- Tiered storage.
	- On-premises cache & low-latency file access.

---

## Tape Gateway
- Some companies have backup processes using physical tapes. -> With Tape Gateway, companies use the same processes but, in the cloud.
- Virtual Tape Library(VTL) backed by [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|Amazon S3]] and Glacier.
- Back up data using existing tape-based processes(and iSCSI interface).
- Works with leading backup software vendors.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20250113090148.png]]