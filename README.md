https://skillbuilder.aws/  for free learning AWS [.](https://gist.github.com/AWScommunity/33ab6119dcdeffa149f245f3257fd889#comments)
![Untitledfffffff](https://user-images.githubusercontent.com/109033173/192111690-0812fa89-41e8-447d-81d8-de7e122c28dc.png)
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

![image](https://user-images.githubusercontent.com/109033173/212552499-4d611ffc-5af3-4092-bcfc-5114a9484ad1.png)
---
![image](https://user-images.githubusercontent.com/109033173/188077200-bc536f61-4776-4935-86c5-c5567b175d2e.png)
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
3. USe instance storage to handle files uploaded by your users. Since its more secure than EBS vol, you can isolate any malicious fies from infecting your server. (X)----
 
When creating new EC2 instance, we can access it from public internet BY auto-assigning to it new public IP address.

How does security group protect your cloud infrastructure? Wrong ans- traffic is allowed to flow betn AWS services but you must add rules to expose ports to public internet. HINT is: A security group with no outbound rules will also block that resources from reaching out to other AWS service endpoints. 

---

An new CIO joins your company and implements a new company policy that all EC2 instances must have encryption at rest. What is the quickest and easiest way to apply this policy to your existing EC2 instances?

In the AWS console, click on the EC2 instances, click actions and click encrypt EBS voulmes.

Create a snapshot of the EC2 volume. Then create a copy of that volume, checking the box to enable encryption. Create an AMI of the copied snapshot and then redeploy the EC2 instance using the encrypted AMI. Delete the old EC2 instance. (Ans)

---

![image](https://user-images.githubusercontent.com/109033173/185830254-038e4876-beeb-45ff-9026-103df622dccd.png)

---
![image](https://user-images.githubusercontent.com/109033173/185744444-ed1e7198-e582-4199-b1a2-a7dc6970eae6.png)

---
NOT too IMP
![image](https://user-images.githubusercontent.com/109033173/187847252-1f3b7709-04bb-4a34-9c3e-271a6b92553e.png)

---
about SQS- additional note other than my pownotes
![image](https://user-images.githubusercontent.com/109033173/186567385-af686d8a-27de-43d8-9d58-13939dba2739.png)
---
![image](https://user-images.githubusercontent.com/109033173/193422322-b40f7d08-68b7-4d6f-8a3e-faaf23aa1606.png)

![image](https://user-images.githubusercontent.com/109033173/192141241-258f9499-d4de-42c7-9b13-fe79d3c043b3.png)

![image](https://user-images.githubusercontent.com/11883023/184070149-17cad737-a8be-4f99-b4f8-569f5b99c8a4.png)
aaaa

![image](https://user-images.githubusercontent.com/11883023/184070191-691e28c7-830a-473e-9e8c-cb9714ae3777.png)

Coding can be compared to writing cooking recipes. A recipe in this analogy is the program and the cook is the computer. A recipe is a list of instructions for a cook to follow and a program is a list of instructions for a computer to execute.    There are also not a lot of unexpected things to plan for in a recipe while a computer program will have many. Regardless of its simplicity, it is a good way to show how a computer carries out a list of instructions sequentially. It also shows where one instruction line can use any result from executing prior instruction lines.

I also like this analogy because of all the ready items and tools that you can use in your recipes — like the cake mix that you can use to make cupcakes and that specially-shaped pan that makes it so much easier to create cupcakes.

The use of ready items and tools is like including and using a package of code written by others in your own code.

````
// The making of a cupcake// First steps:
$ npm install cake-mix$ npm install cupcake-pan
NPM is the package manager for Node.js, which a very popular framework for writing JavaScript applications. In this analogy, Node.js is like the kitchen itself. It allows you to execute lines in your recipes by using built-in modules like your oven and sink.
````
Speaking of unhealthy food, this next analogy is for learning how to code and is compared to eating habits. I particularly LOVE this analogy and what it conveys because it helps me to stay on track in my code learning journey. For me, this began in high school and will continue until my brain reaches its last instruction: die();

Learning To Code
Learning to code is like trying to lose weight. This analogy applies to learning anything really, but learning to code is a special match here.

“Losing Weight” is a negative term. We should really call it “Gaining Health.” In that sense, it is very much comparable to “Gaining Knowledge.” The educational resources you have available to you are like your food options. Some are just okay, some are great, and some are completely bad for you. Eating healthy and exercising are the main two activities that will help you gain health. Similarly, consuming good educational resources and practicing coding by hand are the main two activities that will help you gain good coding knowledge.

So how do you learn “healthy”? When you commit to eating healthy, you use filters like organic, local, reduced-fat, grass-fed, and non-gmo. It is exactly the same with healthy educational resources except these labels are not yet as clear. I hope educational resources will someday have verifiable and relevant labels too. Maybe labels like “not-sponsored,” “no-marketing,” “approved-by-experts,” “tightly-edited,” and “dragons-ahead.”

Yet, instead of filtering by the content, you can easily filter by the good brands. I do that with food too. I know and trust a few brands and I mostly use those. It is easier. With educational resources, there are some brands (publications and people) that you should just follow all the time.

After filtering your knowledge intake to only the good resources, you just need to exercise! Practice everything you learn, but not just by re-doing exactly what you learned. Also challenge yourself to do something slightly different around the topics that you learned. If you are lucky, you will get stuck! Then you will permanently learn something else when you get unstuck.

Exercise is for both the body and the mind.

**Variables**
Variables are used in computer programs to hold data. This is a very simplified statement and it is by many measures simply wrong.

Variables do not hold data. They just point to it. Data is held in the computer’s memory. You can compare variables to the labels you place on your email messages (or notes, or files).

All code samples in this article are written in JavaScript. JavaScript is a very easy to learn computer language.

In Gmail, a label is a pointer to an email or a list of emails. Many labels can point to the same email. This is similar to assigning another variable to an existing variable:

let work = [email1, email2, email3];let important = work;
Both work and important are now labels that point to the exact same list of emails.

Some variables represent constant references. They cannot be changed. This is like the “sent” label in Gmail. While we can change the work label above and make it point to a different list of emails, we cannot change the label sent. You cannot point the sent label to a different list of emails. You can only make it point to more emails.

const sent = [];
// You cannot change the meaning of sent now// But you can add more values to it:
sent.push(new Email());
Errors and Exceptions
A programmer’s expertise is largely about how to deal with errors. Expert programmers love errors because, for them, errors mean progress.

Sometimes we expect to see these wonderful red messages and if we do not we know that the code is simply wrong!

I love the phrase “listen to your code” because I think code evolves by communicating to us using errors.

This is exactly like raising kids.

The most important parenting concept that I realized, with practice, is how kids communicate by misbehaving. This is because they do not have a logical brain yet. I think programs do the exact same thing. They also communicate by misbehaving (producing errors) because programs are not completely logical. Your task as a programmer is to add more logic in the code to handle the cases that originally produced errors. This is just like how a parent’s task is to teach the misbehaving kid what is wrong with that bad behavior and what to do differently next time.

Some errors are not recoverable and a program encountering those should just exit (and be rebooted). This is like if your heart stops. There is not much that can be done except to reboot it with an electric shock. This is why we monitor our programs and reboot them when they get to that state. Luckily, the process of rebooting a program is not as dramatic.

Most errors that happen during the early development of programs help improve these programs so that the errors never happen. This is how good kids are raised. They do not repeat the misbehaving because now they have good logic to guide them in a good direction.

Some errors evolve to be exceptions. Exceptions are expected errors. Errors that we can plan for and recover from. The best coding example here is a Network Connection error while we make a program, for example, download some data. This is very much expected because we know network connections could be unreliable so we plan for that error. When that error happens, let’s label the task of downloading that data as incomplete. Queue it somewhere, and re-try it at a later time (see below for an analogy for queuing).

What we did with this planned exception is give the computer a different set of instructions (a different recipe) to do when that error happens. We do exactly that with our kids as well. We give them instructions about what to do in certain future scenarios that we expect (or fear in this case).

// Hey kidsif (stranger.offersYou(chocolate)) {  doNotAccept();  doNotTalkTo(stranger);  walkAway();}
if (stranger.triesToForceYouToDoSomething()) {  screamFor(help);  runAway();  call(911);}
