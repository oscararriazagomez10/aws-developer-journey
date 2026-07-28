# IAM AND AWS CLI Notes

## 1. What is AWS IAM?

AWS Identity and Access Management (IAM) is a service that allow you to securely manage identities and control access to aws resources.

IAM defines:

- who can access aws resources.
- what actions they can perform.
- which resources they can access.

IAM is a global AWS service and does not belong to a specific Region.

---

# 2. IAM Core Concepts

AWS IAM is based on four main components:

- Users
- Groups
- Roles
- Policies

These components work together to control permissions.

---

# 3. IAM Users

## Definition

AN IAM Users is an identity inside an AWS account that represents a person or application.

A user can have:

- Username.
- Password for console access.
- Access keys for programmatic access.
- Assigned permissions.

---

## Example

A company has developer who needs access to AWS resources.

Instead of sharing the root account, the company creates:

```
Developer User
      |
      |
Permissions
      |
      |
EC2 + S3 Access
```

---

## Why is it important?

Creating individual IAM users improves security because each person has their own credentials and permissions.

--- 

# 4. IAM Groups 

## Definition 

An IAM Group is a collection of IAM userts that share the same permissions.

Permissions are assigned to the group instead of individual users.

--- 

## Example

A company creates:

```
Developers Group

User 1
User 2
User 3

Permissions:
- Read EC2
- Access S3
```

All users inside the group inherit those permissions.

---

## Benefits

- Easier permission management.
- Consistent access control.
- Better organization.

---

# 5. IAM Policies

## Definition

An IAM policy is a document that defines permissions.

Policies specify:

- Actions Allowed or denied.
- Resources affected.
- Conditions.

---

## Example

A policy can allow:

```
Action:
Read objects from S3

Resource:
Company bucket
```
---

## Types of policies

### AWS Managed Policies

Policies created and maintained by aws

Example:

```
AmazonS3ReadOnlyAccess
```

---

### Customer Managed Policies

Policies created and managed by the customer.

They allow more specific permissions.

---

# 6. IAM Roles

## Definition

An IAM Role is a identity that provides temporany permissions to users, applications or AWS services.

Unlike users, rolews do not have permanent credentials.

---

## Example 

An EC2 instance needs access to an S3 bucket

Instead of storing access keys inside the server:

```
EC2 Instance

      |
      |
IAM Role

      |
      |
S3 Access
```
The role provides temporary permissions securely.

---

# 7. Authentication vs Authorization

##  Authentication 

 Authentication  answers:

 "Who are you?

Example:

Logging into AWS with username and password.

---

## Authorization

Autorization answers:

"What can you do?"

Example:

A user can access S3 but cannot delete IAM users.

---

# 8. Principle of least Privilege

## Definition

The Principle of Least Privilege means giving users only permissions they need to perform their tasks.

---

## Example

A developer who only needs to read files from S3 not have permission to delete  buckets.

Bad practice:

```
Administrator Access
```
Better practice:

```
S3 Read Only Access
```

# 9. Root User Security

The Root User is the original account created when an AWS account is created.

It has complete access to all AWS resources.

---

## Best Practices

- Do not use the root account for daily tasks.
- Enable MFA.
- Create IAM users for normal operations.
- Protect root credentials.

---

# 10. Multi-Factor Authentication (MFA)

## Definition 

MFA adds an additional security layer by requiring more than one authentication method.

Example:

Something you know:

```
Password
```
Something you have:

```
Authenticator application
```

---

## Benefits

- Protects accounts againts stole passwords.
- Improves AWS account security.

---

# 11. AWS CLI

## Definition

AWS Command Line Interface (CLI ) is a tool that allows users to interact whith AWS services using commands from a terminal.

---

## Advantages

- Automation.
- Faster resource management.
- Integration with scripts.
- Userful for developers and administrators.

---

# 12. AWS CLI Configuration

The main commnads used to configure AWS CLI is:

```
aws configure
```
This command requires:

- Access Key ID.
- Secret Access Key.
- Default Region.
- Output format.

---

# 13. Userful AWS CLI Commands

Check current AWS identity:


```
aws sts get-caller-identity
```
List IAM users:

```
aws iam list-users
```
List S3 buckets:

```
aws s3 ls
```
---

# Key Takeaways

After completing this module, I understand:

✅ How AWS manages identities and permissions.

✅ The difference between IAM Users, Groups, Roles and Policies.

✅ How authentication and authorization work.

✅ How to configure and use AWS CLI.

✅ The importance of AWS security best practices.

