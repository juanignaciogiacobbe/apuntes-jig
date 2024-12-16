# [Amazon S3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md) Object Encryption
- You can encrypt objects in S3 buckets using one of 4 methods:
	- Server-Side Encryption(SSE):
		- Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3) – Enabled by Default 
			- Encrypts S3 objects using keys handled, managed, and owned by AWS. 
		- Server-Side Encryption with KMS Keys stored in AWS KMS (SSE-KMS) 
			- Leverage AWS Key Management Service (AWS KMS) to manage encryption keys .
		- Server-Side Encryption with Customer-Provided Keys (SSE-C) 
			- When you want to manage your own encryption keys.
	- Client-Side Encryption.


!!! important Server Side Encryption-S3
> - Encryption using keys handled, managed, and owned by AWS.
> - Object is encrypted server-side,
> - Encryption type is AES-256.
> - Must set header "x-amz-server-side-encryption": "AES256".
> - Enabled by default for new buckets & new objects.

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241203105822.png)

---

!!! important Server-Side Encryption-KMS
> - Encryption using keys handled and managed by AWS KMS.
> - Advantages: User control + Audit key usage using CloudTrail.
> - Objects is encrypted server side.
> - Must set header "x-amz-server-side-encryption": "aws:kms"

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241203110108.png)


!!! warning SSE-KMS Limitation
- You may be impacted by the KMS limits.
- When you upload, ir calls the GenerateDataKey KMS API.
- When you download, it calls the Decrypt KMS API.
- You can request a quota increase using the Service Quotas Console.

---


!!! important Server-Side Encryption-C
> - Server-Side encryption using keys fully managed by the customer outside of AWS.
> - Amazon S3 DOES NOT store the encryption key you provide.
> - HTTPS must be used.
> - Encryption key must provided in HTTP headers, for every HTTP request made.


![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241203110504.png)

> [!PDF|red] [AWS Certified Solutions Architect Slides v39, p.314](AWS/Slides/AWS%20Certified%20Solutions%20Architect%20Slides%20v39.pdf#page=314&selection=8,0,14,15&color=red)
> > Amazon S3 Encryption – Client-Side Encryption


