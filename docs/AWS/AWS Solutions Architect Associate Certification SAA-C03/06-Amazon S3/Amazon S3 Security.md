
> [[AWS/Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|!WARNING]] Security
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

!!! note "JSON Based Policies"
> - Resources: Buckets and Objects.
> - Effect: Allow or Deny.
> - Actions: Set o API to Allow or Deny.
> - Principal: The account or user to apply the policy to.


!!! warning "Use S3 Bucket for Policy to:"
- Grant public access to the bucket.
- Force objects to be encrypted at upload.
- Grant access to another account(Cross account).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241203100557.png]]