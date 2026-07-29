# Commands Executed

## Check AWS CLI Version

```bash
aws --version
```

Purpose:

Verify that AWS CLI is installed correctly

---

## Configure AWS CLI

```bash
aws configure
```

Purpose:

Configure authentication credentials and the default AWS Region.

---

## Verify Current Identity

```bash
aws sts get-caller-identity
```

Purpose:

Verify that AWS CLI is authenticated successfully

---

## List IAM Users

```bash
aws iam list-users
```

Purpose:

Display all IAM users in the AWS account.

---

## List S3 Buckets

```bash
aws s3 ls
```

Purpose:

Display all Amazon S3 buckets available in the account.

---

## Create an IAM User

```bash
aws iam create-user --user-name developer-user

```
Purpose:
Create a new IAM user using AWS CLI.

---

## Get IAM User Information

```bash
aws iam get-user --user-name developer-user

```
Purpose:

Retrieve information about a specific IAM user.

---

## Delete an IAM User

```bash
aws iam delete-user --user-name developer-user

```
Purpose:

Delete an IAM user from the AWS account

---

# IAM Group Management

## List IAM Groups

```bash
aws iam list-groups

```
Purpose:

Display all IAM groups in the AWS account.

---

## Create an IAM Group

```bash
aws iam create-group --group-name Developers

```
Purpose:

Create a new IAM group to manage permissions more efficientrly

---

## Add User to a Group

```bash
aws iam add-user-to-group \
--user-name developer-user \
--group-name Developers
```
Purpose:

Add an IAM user to an existing group.

---

## List Users Inside a Group

```bash
aws iam get-group --group-name Developers
```
Purpose:

Display users belonging to a specific IAM group.

---

# IAM Policy Management

## List User Policies

```bash
aws iam list-attached-user-policies \
--user-name developer-user

```
Purpose:

Show policies attached to an IAM user.

---

## Attach a Policy to a User

Example:
```bash
aws iam attach-user-policy \
--user-name developer-user \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```
Purpose:

Assign permissions to an IAM user using an AWS managed policy.

---


## Remove a Policy from a User
```bash
aws iam detach-user-policy \
--user-name developer-user \
--policy-arn arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
```
Purpose:

Remove permissions from an IAM user.

---

# AWS Account Information
## List AWS Regions
```bash
aws ec2 describe-regions

```
Purpose:

Display AWS Regions available for the account.

---

#  AWS CLI Documentation

## AWS CLI Help

```bash
aws help

```
Purpose:

Display general AWS CLI documentation.

---

## IAM CLI Help
```bash
aws iam help

```
Purpose:

Display IAM-specific AWS CLI commands and options.

---

## Best Practices Applied

During this lab, the following AWS CLI security practices were followed:

- Never share AWS Access Keys.
- Avoid storing credentials in source code.
- Use IAM users instead of Root credentials.
- Apply the Principle of Least Privilege.
- Remove unused resources after testing.




