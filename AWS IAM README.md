<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Nii OB  
**Email:** niiobdavid@gmail.com

---

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS IAM to control access and permission settings in my AWS account. 
I'm doing this project to learn about Cloud Security from the absolute foundations. Every company thinks about access permissions, and there are even entire jobs called 'IAM Engineers' focused on the skills I'm about to build today.

### Tools and concepts

Services I used were Amazon EC2 and AWS IAM. Key concepts I learnt include IAM users, user groups, policies, and account aliases.
I also learnt to use the Policy Simulator, and how JSON policies work.
Also learnt to launch, and tag an instance as well as create and log into other user accounts.

### Project reflection

This project took me approximately 20mins minus demo time. 
The most challenging part was understanding the IAM policy since it was written in JSON and contained multiple statements. 
It was most rewarding to see permission denied when the intern tried to delete the production instance, which means the  IAM access management worked.

---

## Tags

### What I did in this step

In this step, I will launch 2 EC2 instances because I need to boost NextWork's computing power as I'm expecting more users and website traffic over the summer break.

### Understanding tags

Tags are organisational tools that allow users to label their resources.
They are helpful for grouping resources, cost allocation, and applying policies for all resources with the same tag.

### My tag configuration

The tag I’ve used on my EC2 instances is called Env = environment. 
The value I’ve assigned for my instances are production and development..

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will use IAM policies to control the access level of the new NextWork intern because they should have access to the development environment( dev instance) but NOT the production environment.

### Understanding IAM policies

IAM Policies are like rules that determine who can do what in the AWS account.
I am using policies today to control who has access to the production instance.

### The policy I set up

For this project, I’ve set up a policy using JSON.

### Policy effect

I’ve created a policy that allows the policyholder (intern) to have permission to do anything they want to any instance tagged "development". 
They can also see information for any instance, but they are denied access to deleting/creating tags for any instance as well.

### Understanding Effect, Action, and Resource

In a JSON policy; 
Effect = whether or not the policy is allowing/denying an action. 
Action = what the policy holder can or cannot do. 
Resource = the specific resources that the policy relates to.

---

## My JSON Policy

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will set up an Account Alias (nickname for the AWS account's console) because it makes it simpler for users to log in.

### Understanding account aliases

An account alias is basically a nickname for the AWS account that replaces the long account ID.
This makes it easier to reference my account.

### Setting up my account alias

Creating an account alias took me about 10 secs. Now, my new AWS console sign-in URL is https://nextwork-alias-nii.signin.aws.amazon.com/console.

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will set up 2 users (IAM users and IAM user groups).
This is because IAM users are like logins for people that want access to the AWS account, while user groups are like folders to manage users that have the same level of access.

### Understanding user groups

IAM user groups are like folders that collect IAM users so permission settings can be applied at the group level.

### Attaching policies to user groups

I attached the policy I created to this user group, which means any user created inside this group will automatically get the permissions attached to the NextWorkDevEnvironmentPolicy IAM policy.

### Understanding IAM users

IAM users are people or entities that have access/ can log in to an AWS account.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to email sign-in instructions to the user, and the second way is to download .csv file with the sign-in details inside.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that the intern is already denied access to panels on the main AWS dashboard. This was because I only set up permissions to the development EC2 instance, so the intern won't have access to even see anything else.

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log into my own AWS account as the intern, and test access to the production and development instances because I want to make sure the intern doesn't have the ability to do anything that affects the production environment.

### Testing policy actions

I tested my JSON IAM policy by attempting to stop both the development and production instances. 

### Stopping the production instance

When I tried to stop the production instance, I was met with an error. This was because the production instance is tagged with the 'production' label, which is out of the scope of the permission policy, which allows interns to do things to the development instances.

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, the instance state successfully changed to Stopping, then Stopped. 
This was because the permission policy allows the users in the NextWorkDevEnvironmentPolicy (which includes the intern) to stop instances.

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to test my permission policies in a safer and more controlled way with a tool called IAM Policy Simulator. 
I'm doing this because logging into AWS accounts as other users and stopping instances is a bit disruptive.
.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool that allows for simulating actions and testing permissions by defining a specific user/group/role. It's useful for saving time when testing permissions, and no more logging into other user accounts, nor stopping resources.

### How I used the simulator

I set up a simulation for whether the dev user group has permission to StopInstances or DeleteTags. The results were denied for both and I had to adjust the scope to the ones tagged 'development'.
Once the tag was applied, permission was allowed.

![Image](http://learn.nextwork.org/genuine_navy_mysterious_monkey/uploads/aws-security-iam_069d8a621)

---

---
