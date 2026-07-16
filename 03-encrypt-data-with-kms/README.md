<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Encrypt Data with AWS KMS

**Project Link:** [View Project](http://nextwork.ai/projects/aws-security-kms)

**Author:** olokunde.o@gmail.com  
**Email:** olokunde.o@gmail.com

---

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_w0x1y2z3)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS Key Management Service (KMS) to create encryption keys and protect data stored in Amazon DynamoDB. The goal is to learn how data encryption works in AWS, manage access to encrypted resources, and apply cloud security best practices.

### Tools and concepts

Services I used include AWS Key Management Service (KMS), Amazon DynamoDB, and AWS IAM. Key concepts I learnt include encryption, customer-managed KMS keys, data encryption at rest, transparent data encryption, IAM users and permissions, key policies, and how KMS controls access to encrypted data.

### Project reflection

This project took me approximately 2 hours. The most challenging part was configuring the KMS key permissions and understanding how key policies work with IAM users. It was most rewarding to successfully encrypt a DynamoDB table and verify that only authorized users could access the encrypted data.

I chose to do this project today because I wanted to gain hands-on experience with AWS KMS, encryption, and securing cloud data. This project helped me understand how KMS works with DynamoDB and IAM to protect sensitive information. Something that would make learning with NextWork even better is including more real-world security scenarios and additional challenge exercises to reinforce the concepts.

---

## Encryption and KMS

Encryption is the process of converting readable data into an unreadable format (ciphertext) so that only authorized users with the correct encryption key can access it. Companies and developers do this to protect sensitive data, maintain privacy, and prevent unauthorized access. Encryption keys are unique digital codes that encrypt and decrypt data, ensuring only users with the correct permissions can read the original information.

AWS KMS is a managed AWS service that allows you to create, store, and manage encryption keys used to protect data across AWS resources. Key management systems are important because they securely store encryption keys, control who can use them, simplify encryption management, and help organizations protect sensitive data while meeting security and compliance requirements.

Encryption keys are broadly categorized as symmetric and asymmetric. I set up a symmetric key because it uses a single key for both encryption and decryption, making it faster and more efficient for encrypting data in DynamoDB. Symmetric keys are commonly used for protecting large amounts of data in AWS services.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_a2b3c4d5)

---

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is a fully managed NoSQL database service provided by AWS. It is designed to store and retrieve data quickly and efficiently while automatically scaling to handle large amounts of traffic.

The different encryption options in DynamoDB include Amazon DynamoDB owned keys, AWS managed keys, and customer managed keys stored in AWS KMS. Their differences are based on who manages the encryption key and how much control you have over it. Amazon DynamoDB owned keys are fully managed by DynamoDB, AWS managed keys are managed by AWS KMS with limited customer control, while customer managed keys give you full control over key management, permissions, and policies. I selected the customer managed key ("Stored in your account, and owned and managed by you") because it provides the highest level of control and security for encrypting my DynamoDB table.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_q8r9s0t1)

---

## Data Visibility

Rather than controlling who has access to the key, KMS manages user permissions by using key policies and IAM policies to define which users or roles can perform actions such as encrypting or decrypting data with the key.

Despite encrypting my DynamoDB table, I could still see the table's items because I have permission to use the KMS key. DynamoDB uses transparent data encryption, which means it automatically decrypts the data for authorized users when they access it.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_c0d1e2f3)

---

## Denying Access

I configured a new IAM user to test access to my encrypted DynamoDB table. I granted the user the AmazonDynamoDBFullAccess policy, but not permission to use my KMS key, so the user cannot decrypt the encrypted data.

After accessing the DynamoDB table as the test user, I encountered an "Access Denied" error because the user did not have permission to use the KMS key to decrypt the data. This confirmed that KMS encryption protects the table by allowing only authorized users to access its contents.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_w0x1y2z3)

---

## EXTRA: Granting Access

To let my test user use the encryption key, I added the user as a key user in the KMS key policy. My key's policy was updated to allow the user to perform cryptographic actions such as encrypting and decrypting data with the key.

Using the test user, I retried accessing the encrypted DynamoDB table after granting it permission to use the KMS key. I observed that I could successfully view the table's data, which confirmed that the updated KMS key policy allowed the user to decrypt and access the encrypted information.

Encryption secures data instead of just controlling who can access it. I could combine encryption with IAM policies and roles to ensure that only authorized users can access and decrypt sensitive data.

![Image](http://nextwork.ai/determined_purple_witty_eagle/uploads/aws-security-kms_feffb2fb8)

---

---
