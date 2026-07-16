<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-iam)

**Author:** olokunde.o@gmail.com  
**Email:** olokunde.o@gmail.com

---

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

### Project overview

In this project, I will demonstrate how to use AWS Identity and Access Management (IAM) to securely manage access to AWS resources by creating EC2 instances, IAM policies, user groups, and users. I'm doing this project to learn cloud security best practices and how to control user permissions in AWS.

### Tools and concepts

Services I used were Amazon EC2 and AWS Identity and Access Management (IAM). With EC2, I launched and managed virtual servers for both the development and production environments. With IAM, I created policies, user groups, users, and an account alias to securely control access to AWS resources. Key concepts I learnt include launching EC2 instances, using tags to organize resources, creating and attaching IAM policies, managing permissions with user groups, applying the principle of least privilege, testing access with an IAM user, and validating permissions using the IAM Policy Simulator.

### Project reflection

This project took me approximately 2 hours to complete. The most challenging part was understanding how IAM policies, user groups, and permissions work together to control access to AWS resources. It was most rewarding to see the policy work correctly by allowing access to the development instance while denying access to the production instance, reinforcing my understanding of AWS security best practices.

---

## Tags

### What I did in this step

In this step, I will launch two Amazon EC2 instances for the production and development environments because they provide the virtual computing resources needed to support applications and allow me to practice managing cloud infrastructure in AWS.

### Understanding tags

Tags are organizational labels that help identify, categorize, and manage AWS resources. In this project, they are used to distinguish between the production and development EC2 instances.

### My tag configuration

The tag I've used on my EC2 instances is called Env. The values I've assigned for my instances are production for the production instance and development for the development instance.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

### What I did in this step

In this step, I will create an IAM policy that grants access to the development EC2 instance while restricting access to the production instance because this helps enforce security by ensuring users only have the permissions they need to perform their tasks.

### Understanding IAM policies

IAM policies are permission rules that control what actions users, groups, or roles can perform on AWS resources. They help enforce secure access by allowing or denying specific actions.

### The policy I set up

For this project, I've set up a policy using JSON because it provides a clear and flexible way to define permissions for AWS resources.

### Policy effect

I've created a policy that grants access to the development EC2 instance, allows users to view EC2 resources, and denies the ability to create or delete tags, ensuring secure and controlled access.

### Understanding Effect, Action, and Resource

The Effect, Action, and Resource attributes of a JSON policy determine how permissions are applied. Effect specifies whether a request is allowed or denied, Action defines the AWS operations that can be performed, and Resource identifies the AWS resources the policy applies to.

---

## My JSON Policy

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_1c864649)

---

## Account Alias

### What I did in this step

In this step, I will create an AWS Account Alias because it simplifies the AWS console login process by replacing the account ID with a memorable name.

### Understanding account aliases

An account alias is a friendly name for an AWS account that replaces the account ID in the sign-in URL, making it easier for users to remember and access the AWS Management Console.

### Setting up my account alias

Creating an account alias took me about 2 minutes. Now, my new AWS console sign-in URL is https://nextwork-alias-olokunde.signin.aws.amazon.com/console, which is much easier to remember and share than the default account ID-based URL.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### What I did in this step

In this step, I will create an IAM user group and an IAM user because this allows me to manage permissions efficiently and provide the new intern with secure access to the AWS account based on their role.

### Understanding user groups

IAM user groups are collections of IAM users that allow administrators to manage permissions for multiple users at once by assigning policies to the group instead of to each user individually.

### Attaching policies to user groups

I attached the policy I created to this user group, which means all users in the group inherit the same permissions. This simplifies access management and ensures they can work in the development environment without having access to production resources.

### Understanding IAM users

IAM users are individual accounts created in AWS for people or applications that need access to AWS resources. They use unique credentials to sign in and receive permissions either directly or through IAM user groups.

---

## Logging in as an IAM User

### Sharing sign-in details

The first way is to download and share the user's sign-in credentials securely. The second way is to send the sign-in instructions to the user's email address.

### Observations from the IAM user dashboard

Once I logged in as my IAM user, I noticed that some AWS console features were inaccessible and showed "Access Denied." This was because the IAM user had limited permissions based on the IAM policy attached to its user group, following the principle of least privilege.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

### What I did in this step

In this step, I will log in as the IAM user and test access to both EC2 instances because I need to confirm that the user has the correct permissions for the development environment and is restricted from the production environment.

### Testing policy actions

I tested my JSON IAM policy by trying to stop both EC2 instances. The production instance was protected by the policy, while the development instance could be stopped successfully, demonstrating that the policy enforced the intended access controls.

### Stopping the production instance

When I tried to stop the production instance, the request was denied because my IAM user did not have permission to manage production resources. The attached IAM policy only allows actions on the development environment.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_0e7a9d6a)

### Stopping the development instance

Next, when I tried to stop the development instance, AWS allowed the action and the instance began stopping. This was because the IAM policy specifically permits EC2 actions on resources tagged as the development environment.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_1811801c)

---

## IAM Policy Simulator

To extend my project, I'm going to use the IAM Policy Simulator to validate my IAM policy and test user permissions. I'm doing this because it allows me to verify access securely without affecting my AWS resources.

### Understanding the IAM Policy Simulator

The IAM Policy Simulator is a tool for testing IAM policies and user permissions in a safe environment. It's useful for confirming that access controls are configured correctly without affecting live AWS resources.

### How I used the simulator

I set up a simulation for the development EC2 instance using the IAM Policy Simulator. The results helped me identify that some permissions were not configured as expected, so I adjusted the IAM policy and reran the simulation until the correct access was granted.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-iam_069d8a621)

---

---
