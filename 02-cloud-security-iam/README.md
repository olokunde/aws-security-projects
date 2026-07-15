# Cloud Security with AWS IAM

## Overview
Implemented tag-based access control in AWS so an intern user could
manage the development environment while being blocked from production
— applying the principle of least privilege.

## Services & Concepts
Amazon EC2 · AWS IAM (policies, users, groups) · JSON policy conditions
· tag-based access control · IAM Policy Simulator

## What I Built
- Launched two EC2 instances tagged `Env: production` and `Env: development`
- Wrote a JSON IAM policy allowing EC2 actions only on `development`-tagged
  resources, and explicitly denying tag changes — so production can't be
  relabelled to bypass the restriction
- Created an IAM group and user, then tested access in an incognito session
- Validated permissions safely using the IAM Policy Simulator, without
  touching live resources

## Result
- Attempt to stop the **production** instance → "not authorized" (as intended)
- Attempt to stop the **development** instance → stopped successfully

## Full Documentation
📄 [Read the full project walkthrough on NextWork](https://nextwork.ai/determined_purple_witty_eagle/docs/aws-security-iam)
