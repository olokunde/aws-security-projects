<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-secretsmanager)

**Author:** olokunde.o@gmail.com  
**Email:** olokunde.o@gmail.com

---

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to secure application credentials using AWS Secrets Manager instead of hardcoding them into source code. I'm doing this project to learn secure secrets management, prevent credential exposure in GitHub repositories, and apply AWS security best practices used in real-world cloud applications.

### Tools and concepts

Services I used were AWS Secrets Manager, GitHub, Git, and Python with the Boto3 SDK. Key concepts I learnt include securely storing and retrieving secrets, replacing hardcoded credentials with Secrets Manager, resolving Git merge conflicts, using Git rebase and push, and following security best practices to keep sensitive credentials out of source code.

### Project reflection

This project took me approximately 2–3 hours. The most challenging part was resolving the Git merge conflict and rebasing the commit history. The most rewarding part was successfully securing the application with AWS Secrets Manager and pushing the cleaned repository to GitHub.

I chose to do this project today because I wanted to improve my cloud security skills and gain hands-on experience with AWS Secrets Manager. Something that would make learning with NextWork even better is adding more troubleshooting tips for common Git and merge conflict issues.

---

## Hardcoding credentials

It is unsafe to expose credentials in code because anyone with access to the source code can steal them and use them to access AWS resources without authorization. This could lead to data breaches, resource deletion, financial loss, and compromise of the entire cloud environment. Using a secure service like AWS Secrets Manager helps protect sensitive credentials from being exposed.

I've set up the initial configuration with example AWS Access Key ID, Secret Access Key, and AWS Region values in config.py. These credentials are just examples because they are not real AWS credentials and are only used to demonstrate why hardcoding secrets in code is insecure.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

As an extension for this project, I also decided to run the web app locally using my own AWS credentials. To set up my virtual environment, I installed the packages listed in requirements.txt, including boto3, FastAPI, and Uvicorn, which are needed for the application to communicate with AWS and run the web server.

When I first ran the app, I ran into an error because it was using the example AWS credentials in config.py. This resulted in an InvalidAccessKeyId error, which means the application couldn't authenticate with AWS since the access key was not valid.

To resolve the InvalidAccessKeyId error, I updated the config.py file by replacing the sample AWS credentials with my own IAM Access Key ID, Secret Access Key, and the correct AWS region. The file now contains my real AWS credentials, allowing the application to authenticate with AWS and securely connect to my S3 resources.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

Once I updated the web app code with credentials, I forked the repository because I wanted my own copy of the project on GitHub, where I could make changes and publish my work without affecting the original repository. A fork is different from a clone because a fork creates an online copy in my GitHub account, while a clone creates a local copy on my computer for development.

To connect my local repository to the forked repository, I updated the origin remote with my GitHub repository URL. Then I used git add and git commit to stage and save my changes. Finally, git push uploaded the project to my GitHub repository.

GitHub blocked my push because it detected hardcoded AWS credentials in the code. This is a good security feature because it prevents sensitive information from being exposed in public repositories and helps protect AWS accounts from unauthorized access.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

Secrets Manager is an AWS service that securely stores and manages sensitive information such as passwords, API keys, and access credentials. I'm using it to store my AWS Access Key ID and Secret Access Key instead of hardcoding them in my application. Other common use cases include storing database credentials, API keys, and OAuth tokens.

Another feature in Secrets Manager is secret rotation, which means automatically changing secrets on a scheduled basis to improve security. It's useful in situations where sensitive credentials, such as database passwords or API keys, need to be updated regularly to reduce the risk of unauthorized access.

Secrets Manager provides sample code in various languages, like Python, Java, and JavaScript, to help developers retrieve secrets securely. This is helpful because it makes it easy to integrate Secrets Manager into applications without hardcoding sensitive credentials.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

I updated the config.py file to retrieve my AWS credentials from AWS Secrets Manager instead of storing them directly in the code. The get_secret() function will securely connect to Secrets Manager, retrieve the stored credentials, and make them available to the application at runtime.

I also added code to config.py to extract the AWS Access Key ID, Secret Access Key, and AWS Region from the secret retrieved by Secrets Manager. This is important because it allows the application to use the credentials securely at runtime without hardcoding sensitive information in the source code.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

Git rebasing is a way to rewrite Git history. I used it to remove the commit that contained my hardcoded AWS credentials. This was necessary because the credentials were still stored in the repository's commit history, even after I removed them from the code.

A merge conflict occurred during rebasing because both my local branch and the remote branch had changes to config.py. I resolved it by keeping the AWS Secrets Manager code, removing the conflict markers and hardcoded credentials, then running git add config.py and git rebase --continue.

Once the merge conflict was resolved, I verified my hardcoded credentials were no longer in the repository by checking the latest commit on GitHub and confirming that config.py retrieves the credentials from AWS Secrets Manager instead of storing them directly in the code.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---
