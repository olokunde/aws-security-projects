# Project 3: Encrypt Data with AWS KMS

## What I built
Used AWS Key Management Service (KMS) to create a customer-managed symmetric
encryption key, then encrypted an Amazon DynamoDB table with it so the data is
protected at rest.

## How I verified it
- Added a test item to the encrypted table — as an authorized user I could read
  it, because DynamoDB uses transparent data encryption (decrypts automatically
  for users with key permissions).
- Created a test IAM user with AmazonDynamoDBFullAccess but NO KMS key permission.
- Logged in as that user → got an "Access Denied / kms:Decrypt" error trying to
  read the table. Access to the resource is not the same as access to the data.
- As key administrator, added the test user to the KMS key policy → they could
  then decrypt and read the data.

## Key concepts
- Customer-managed keys (CMK) vs AWS-managed keys
- Data encryption at rest
- Transparent data encryption
- **Key policies vs IAM policies** — the key policy controls who can use the key,
  separate from IAM resource permissions
- Least privilege

## Services used
AWS KMS · Amazon DynamoDB · AWS IAM

## Documentation
Full write-up: https://nextwork.ai/determined_purple_witty_eagle/docs/aws-security-kms
