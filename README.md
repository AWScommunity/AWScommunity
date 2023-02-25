Listed on base of priority  [.](https://gist.github.com/AWScommunity/33ab6119dcdeffa149f245f3257fd889#comments)

aws..com bibek...@g 3..3     aws.amazon.com sh..@g 37W..337W..3

[AMAZON account for registering aws cloud architect exams](https://aws.amazon.com/certification/certification-prep/testing/) etc   

and [also for learning cloud practitioner FREE ENROLL in aws skillbuilder](https://explore.skillbuilder.aws/learn/course/12483/play/50113/aws-certified-cloud-practitioner-official-practice-question-set-clf-c01-english) is with sbi.@g 37w.8

---
C L O U D . P R A C T I T I O N E R - code: CLF- CO1 
1.CLOUD CONCEPT (IknowIt) - 26% marks
1.1 WHY cloud? Agility,Elasticity, Flexibility & Security
1.2 TCO 
1.3 AWS Pricing Model, 
1.4 Cost explorer & Trusted Advisor

2. SECURITY & COMPLIANCE - 25%
2.1 HIPAA Compliance

2.2 IAM 
![image](https://user-images.githubusercontent.com/109033173/185743047-ca90154f-f832-4145-a1bc-14b968c20a39.png)

IAM is about needs to deal w administrating diff accounts as dgm. so as in famous yt v in amazon web services channel. 
For eg, if u want s3 to be accessed by say dev account ID345, then simply write s3accessPolicy: true yml for ID345 in that principal aka master aka root aws acc. 

2.3 MFA and User&Groups
![image](https://user-images.githubusercontent.com/109033173/185743032-f91f0896-ec79-4c3a-8008-355e06bde191.png)
achieve single sign-on in principal aka root aws acc by configuring SAML2.0

Now lets get around some tricky situation where for SSO, SAML2.0 is not configured.
 
suppose some X company has employees who need to run internal applications that access company's aws resources. these employees already have user credentials in company's Identity Auth system, WHICH DOESNT SUPPORT SAML2.0 ,and company doesnt want to create seperate IAM user for each company employees.
    SO, IN THIS CASE, SSO setup can be designed by:
 creating custom identity broker application which authenticates employees using existing system, and 
a) uses GetFederationToken API call and passes permission policy to gain temporary access credentials from Security.Token.Service.
b) uses AssumeRole API call to gain temporary role based access to AWS

btw: Federation unlike SSO or unlike authentication is a collection of domains that have established trust. The level of trust may vary, but typically includes authentication and almost always includes authorization. A typical federation might include a number of organizations that have established trust for shared access to a set of resources.
also dyk that while doing IAM in root, you have to grant or deny permissions to individual IAM, or in group ,or do to federated domains.
    
and if we want 50 new employees to have access to S3 buckets with unltd previlege and rest 60 with not, then I simply do: 
create new group adding that 50 and add S3 bucket policy with unltd previlege.

If u want details 1 feet below view of how it works, then go >>
https://user-images.githubusercontent.com/109033173/192111690-0812fa89-41e8-447d-81d8-de7e122c28dc.png

2.4 NACL Network.Access.Control.List
2.5 CloudWatch

2.5 CloudTrail

3 TECHNOLOGY- 33%
Elastic BeanStalk : It handles the auto- provisioning of the infrastructure, deploys the application, handles the load by applying auto scaling, and monitors the application.                             to create artifacts of codes like .jar .exe (novice me thinks- artifact creation is next natural compulsion in case of some s/w, apps but not so, if we are doing some https websites only BUT idk if i am right). then comes writing the sequence of what we did in Lpost2 and creating artifacts, all in one aws pipeline so that it knows what next to do on its own. I've summarized it below, open in new tab: https://giphy.com/embed/2wLc0VnNbFwyRCZn2U

3.1 CloudFormation

3.2 [Opswork](https://www.youtube.com/watch?v=BhNfhHXvhhc)

3.3 [CodeCommit](https://www.youtube.com/watch?v=46PRLMW8otg)

3.4 EC2 - IknowIt
ec2 reserved instances        ec2 spot instances works on solo and on the spot

ec2 dedicated hosts are usually when company wants to migrate n tier web applications to AWS and company wnats to control placement of instances and have visibility to underlying sockets and cores for listening purposes.
```
When using AWS for R&D ahead of planned migration, how do you prevent unexpected increases or spikes in billing?
1.  Using Root AWS acc, enable billing alerts in user preferences. Then use CloudWatch to create billing alarm & set threashold to specific dollar amount for your est monthly charges.  (correct ans)

2.  Using Root AWS acc, activate IAM access to billing information for account. 
Ensure your IAM user have BillingFullAccess Group Policy. Then from billing dashboard, check accrued charge once a day.

3.  Use bill dashboard to create cost budget. Input max amount you want to be charged each mo. 
Any charges that occur over this amount will cause AWS to auto suspend these resources.

4.  If you are using AWS free tier, you will have to confirm usage of any service that goes over AWS free tier limits.
```

3.5 S3
![s3](https://user-images.githubusercontent.com/109033173/221375145-c9aade21-8a6e-49a0-bc4f-1182c6367f9e.png)
 
3.6 AZs & Regions, EdgeLocations
![image](https://user-images.githubusercontent.com/109033173/221374914-ebf2c34c-6aa6-48b4-ab75-34781cb882c7.png)

3.7 SQS
![SQS](https://user-images.githubusercontent.com/109033173/221375039-1f4ef01e-db1c-44fe-a977-944991c8f3b2.png)

3.8 SNS , ELB, VPC(<- look my white note)
3.9 EBS,  Route53

4 BILLING & PRICING - 16%
On Demand Pricing, Dedicated Host, Spot Instances, Billing Alert and Budget,
Billing Support

![image](https://user-images.githubusercontent.com/109033173/212552499-4d611ffc-5af3-4092-bcfc-5114a9484ad1.png)

---
watch this below dgm w that CIDR notes from my Whitepaper
![image](https://user-images.githubusercontent.com/109033173/183240652-76f9f489-b36b-4b9c-952a-49189d5c789c.png)

---
![image](https://user-images.githubusercontent.com/109033173/185744444-ed1e7198-e582-4199-b1a2-a7dc6970eae6.png)

---
![image](https://user-images.githubusercontent.com/109033173/193422322-b40f7d08-68b7-4d6f-8a3e-faaf23aa1606.png)

![image](https://user-images.githubusercontent.com/109033173/192141241-258f9499-d4de-42c7-9b13-fe79d3c043b3.png)

---
cloud soln archi SAA - CO2 quiz solving screenshots, put this way so as to not steal FOCUS from main meats above.
https://user-images.githubusercontent.com/11883023/184070149-17cad737-a8be-4f99-b4f8-569f5b99c8a4.png
https://user-images.githubusercontent.com/11883023/184070191-691e28c7-830a-473e-9e8c-cb9714ae3777.png
https://user-images.githubusercontent.com/109033173/187847252-1f3b7709-04bb-4a34-9c3e-271a6b92553e.png

---
When launching EC2 instance with instance type that supports instance storage, what use case best for instance storage?
1. Instance storage is faster than EBS vol. so, install root of operating sys on this vol to speed up server performance.
2. USe instance storage to serve temp files that require low I/O latency.
3. USe instance storage to handle files uploaded by your users. Since its more secure than EBS vol, you can isolate any malicious fies from infecting your server. (X)
--- 
When creating new EC2 instance, we can access it from public internet BY auto-assigning to it new public IP address.

How does security group protect your cloud infrastructure?
Wrong ans- traffic is allowed to flow betn AWS services but you must add rules to expose ports to public internet. 

HINT is: A security group with no outbound rules will also block that resources from reaching out to other AWS service endpoints. 

--
new CIO joins your company and implements a new company policy that all EC2 instances must have encryption at rest. What is the quickest and easiest way to apply this policy to your existing EC2 instances?

In the AWS console, click on the EC2 instances, click actions and click encrypt EBS voulmes.
Create a snapshot of the EC2 volume. Then create a copy of that volume, checking the box to enable encryption. Create an AMI of the copied snapshot and then redeploy the EC2 instance using the encrypted AMI. Delete the old EC2 instance. (Ans)

---
![image](https://user-images.githubusercontent.com/109033173/180044421-2a5284ba-5783-4e38-a19c-130fa906bf25.png) 
