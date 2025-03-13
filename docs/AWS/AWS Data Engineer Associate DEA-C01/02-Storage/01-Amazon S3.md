# [[AWS/AWS Cloud Practitioner CLF-C02/05-Storage and Databases/01-Amazon Simple Storage Service S3|Amazon S3]] Objects
- Objects(files) have a Key -> The key is the full path(example: `s3://my-bucket/my_folder1/another_folder/my_file.txt`)
- The key is composed of `prefix` + `object name`.
- There's no concept of "directories" within buckets.
- Objects values are the content of the body:
	- Max. Object Size is 5TB. -> If uploading more than 5GB, must use "multi-part upload".


---

## Amazon S3 Security
- User-Based:
	- [[AWS/AWS Cloud Practitioner CLF-C02/06-Security/22- AWS Identity and Access Management IAM|IAM]] Policies -> Which API calls should be allowed for a specific user from IAM.
- Resource-Based
	- Bucket Policies -> Bucket wide rules from the S3 console: allows cross account.
	- Object Access Control List(ACL) -> Finer grain(can be disabled).
	- Bucket Access Control List(ACL) -> Less common(can be disabled).
- An IAM principal can access an S3 object if:
	1. The user IAM permissions ALLOW it OR the resource policy ALLOWS it.
	2. There's no explicit DENY.
- Encryption -> Encrypt objects in Amazon S3 using encryption keys.

### S3 Bucket Policies
- JSON based policies:
	- Resources: Buckets and objects.
	- Effect: Allow or Deny.
	- Actions: Set of API to Allow or Deny.
	- Principal: The account or user to apply the policy to.
- Use S3 bucket for policy to:
	- Grant public access to the bucket.
	- Force objects to be encrypted at upload.
	- Grant access to another account(Cross Account).
