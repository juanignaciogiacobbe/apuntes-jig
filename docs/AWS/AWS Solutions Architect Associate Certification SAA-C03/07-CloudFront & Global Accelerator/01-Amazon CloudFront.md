# Amazon CloudFront


!!! note "Amazon CloudFront"
> Content delivery network (CDN) that allows you to store your content at "edge locations" located all around the world, allowing customers to access your content more quickly.

 - It alone doesn't ensure high availability.
 - Delivers data and applications globally with low latency.
 - Makes content available globally or restricts it based on location.
 - Speeds up delivery of static and dynamic web content. -> Improves read performance(content is cached at the edge) and user experience.
 - DDoS protection(because worldwide), integration with Shield and WAF.


![[cloudfront.png]]
![[edge_loc1.png]]


![[edge_loc2.png]]

![[edge_loc3.png]]


---

## Geo Restriction

- You can restrict who can access your distribution
	- Allowlist: Allow your user to access your content only if they're in one of the countries on a list of approved countries.
	- Blocklist: Prevent your users from accessing your content if they're in one of the countries on a list of banned countries.
- The "country" is determined using a 3rd party Geo-IP database.


---

## Price Class
- You can reduce the number of edge locations for cost reduction.

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227090543.png]]

---

## Cache Invalidations
- In case you update the back-end origin, CloudFront doesn't know about it and will only get the refreshed content after the TTL has expired -> You can force an entire or partial cache refresh(bypassing the TTL) by performing a CloudFront invalidation.
- You can invalidate all files(`*`) or a special path(`/images/*`).

![[AWS/AWS Solutions Architect Associate Certification SAA-C03/img/Pasted image 20241227091024.png]]