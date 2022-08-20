https://skillbuilder.aws/  for free learning AWS [.](https://gist.github.com/AWScommunity/33ab6119dcdeffa149f245f3257fd889#comments)
---
![image](https://user-images.githubusercontent.com/109033173/185743047-ca90154f-f832-4145-a1bc-14b968c20a39.png)
IAM-policy-Ninja post: is about needs to deal w administrating diff accounts as dgm. so as in famous yt v in amazon web services channel. 
For eg, if u want s3 to be accessed by say dev account ID345, then simply write s3accessPolicy: true yml for ID345 in that principal aka master aka root aws acc. 

![image](https://user-images.githubusercontent.com/109033173/185743032-f91f0896-ec79-4c3a-8008-355e06bde191.png)
achieve single sign-on in principal aka root aws acc by configuring SAML2.0

now lets get around some tricky situation where for SSO, SAML2.0 is not configured. 
suppose some X company has employees who need to run internal applications that access company's aws resources. these employees already have user credentials in company's Identity Auth system, WHICH DOESNT SUPPORT SAML2.0 ,and company doesnt want to create seperate IAM user for each company employees.
    SO, IN THIS CASE, SSO setup can be designed by:
 creating custom identity broker application which authenticates employees using existing system, and 
a) uses GetFederationToken API call and passes permission policy to gain temporary access credentials from Security.Token.Service.
b) uses AssumeRole API call to gain temporary role based access to AWS

btw: Federation unlike SSO or unlike authentication is a collection of domains that have established trust. The level of trust may vary, but typically includes authentication and almost always includes authorization. A typical federation might include a number of organizations that have established trust for shared access to a set of resources.
also dyk that while doing IAM in root, you have to grant or deny permissions to individual IAM, or in group ,or do to federated domains.
    and if we want 50 new employees to have access to S3 buckets with unltd previlege and rest 60 with not, then I simply do:
create new group adding that 50 and add S3 bucket policy with unltd previlege.
---
![image](https://user-images.githubusercontent.com/109033173/180044421-2a5284ba-5783-4e38-a19c-130fa906bf25.png)
---
![image](https://user-images.githubusercontent.com/109033173/183808397-daf854b3-6494-4951-8612-cb8df8cf1cac.png)
![image](https://user-images.githubusercontent.com/109033173/185548155-b630d80d-5424-4a56-acd9-85080b390e9b.png) Paas eg is Db aaS
---
CNAME record, A record comes while using DNS ie Route53, 53 is basically port no. related to DNS so
![image](https://user-images.githubusercontent.com/109033173/185548275-db84c85b-180b-4c68-b072-b81e1c76b0d4.png)
---
AWS Elastic Beanstalk handles the auto- provisioning of the infrastructure, deploys the application, handles the load by applying auto scaling, and monitors the application.                             to create artifacts of codes like .jar .exe (novice me thinks- artifact creation is next natural compulsion in case of some s/w, apps but not so, if we are doing some https websites only BUT idk if i am right). then comes writing the sequence of what we did in Lpost2 and creating artifacts, all in one aws pipeline so that it knows what next to do on its own. I've summarized it below, open in new tab: https://giphy.com/embed/2wLc0VnNbFwyRCZn2U

---
watch this below dgm w that CIDR notes from my Whitepaper
![image](https://user-images.githubusercontent.com/109033173/183240652-76f9f489-b36b-4b9c-952a-49189d5c789c.png)
---
Some questions commonly asked in AWS SAA- CO2 Solution Archi Exam:
When using AWS for R&D ahead of planned migration, how do you prevent unexpected increases or spikes in billing?
1.  Using Root AWS acc, enable billing alerts in user preferences. Then use CloudWatch to create billing alarm & set threashold to specific dollar amount for your est monthly charges.  (correct ans)

2.  Using Root AWS acc, activate IAM access to billing information for account. Ensure your IAM user have BillingFullAccess Group Policy. Then from billing dashboard, check accrued charge once a day.

3.  Use bill dashboard to create cost budget. Input max amount you want to be charged each mo. Any charges that occur over this amount will cause AWS to auto suspend these resources.

4.  If you are using AWS free tier, you will have to confirm usage of any service that goes over AWS free tier limits.
---
When launching EC2 instance with instance type that supports instance storage, what use case best for instance storage?
1. Instance storage is faster than EBS vol. so, install root of operating sys on this vol to speed up server performance.
2. USe instance storage to serve temp files that require low I/O latency.
3. USe instance storage to handle files uploaded by your users. Since its more secure than EBS vol, you can isolate any malicious fies from infecting your server. (X)
 ---
 When creating new EC2 instance, we can access it from public internet BY auto-assigning to it new public IP address.
 How does security group protect your cloud infrastructure? Wrong ans- traffic is allowed to flow betn AWS services but you must add rules to expose ports to public internet. HINT is: A security group with no outbound rules will also block that resources from reaching out to other AWS service endpoints. 
 ------
An new CIO joins your company and implements a new company policy that all EC2 instances must have encryption at rest. What is the quickest and easiest way to apply this policy to your existing EC2 instances?

In the AWS console, click on the EC2 instances, click actions and click encrypt EBS voulmes.
Create a snapshot of the EC2 volume. Then create a copy of that volume, checking the box to enable encryption. Create an AMI of the copied snapshot and then redeploy the EC2 instance using the encrypted AMI. Delete the old EC2 instance. (Ans)
---
![image](https://user-images.githubusercontent.com/109033173/185744148-641cc589-3683-4f04-a698-7a15efad02a0.png)
