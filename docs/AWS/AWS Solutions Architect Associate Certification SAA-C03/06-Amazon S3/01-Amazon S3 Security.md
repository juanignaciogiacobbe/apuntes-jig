
> [!WARNING] [AmazonS3](AWS/Cloud%20Practitioner%20(CLF-C02)/05-Storage%20and%20Databases/01-Amazon%20Simple%20Storage%20Service(S3).md) Security
- User-Based:
	- IAM Policies: Which API calls should be allowed for a specific user from IAM.
- Resource-Based:
	- Bucket Policies: Bucket wide rules from the S3 Console -> Allows cross account.
	- Object Access Control List(ACL): Finer grain(can be disabled).
	- Bucket Access Control List(ACL): Less common(can be disabled).
- An IAM principal can access an S3 Object if:
	- The user IAM permissions ALLOW it OR the resource policy ALLOWS it.
	- AND there's no explicit DENY.
- Encryption: 
	- Encrypt objects in Amazon S3 using encryption keys.

# S3 Bucket Policies

> [!IMPORTANT] JSON Based Policies
> - Resources: Buckets and Objects.
> - Effect: Allow or Deny.
> - Actions: Set o API to Allow or Deny.
> - Principal: The account or user to apply the policy to.


> [!WARNING] Use S3 Bucket for Policy to:
- Grant public access to the bucket.
- Force objects to be encrypted at upload.
- Grant access to another account(Cross account).

![](AWS/AWS%20Solutions%20Architect%20Associate%20Certification%20SAA-C03/img/Pasted%20image%2020241203100557.png)