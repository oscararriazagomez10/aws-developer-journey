# 🔐 AWS Security Best Practices

## Overview

Security is one of the most important aspects of cloud computing.

AWS provides multiple security features to protect accounts, identities and resources.

Following security best practices helps reduce risks, prevent unauthorized access and protect sensitive information.

---

# 1. Protect the Root User Account

## Description

The Root User is the account created when an AWS account is created.

It has complete access to all AWS resources and should not be used for daily operations.

---

## Best Practices

- Enable Multi-Factor Authentication (MFA).
- Do not create access keys for the Root User.
- Use IAM users or roles for daily tasks.
- Store Root credentials securely.

---

# 2. Enable Multi-Factor Authentication (MFA)

## Description

MFA adds an additional security layer by requiring a second authentication factor.

Instead of relying only on a password, users must provide another verification method.

---

## Benefits

- Protects accounts against stolen passwords.
- Reduces the risk of unauthorized access.
- Improves account security.

---

# 3. Apply the Principle of Least Privilege

## Description

The Principle of Least Privilege means providing users and applications only with the permissions they need to perform their tasks.

---

## Example

Bad practice:

```
Developer → AdministratorAccess
```

Better practice:

```
Developer → Specific permissions required for their job
```

---

## Benefits

- Reduces security risks.
- Limits potential damage from compromised accounts.
- Improves permission management.

---

# 4. Avoid Sharing Access Keys

## Description

Access keys provide programmatic access to AWS services.

They should never be shared or stored publicly.

---

## Best Practices

- Never upload Access Keys to GitHub.
- Avoid hardcoding credentials in applications.
- Use IAM Roles whenever possible.
- Rotate credentials when necessary.

---

# 5. Use IAM Roles Instead of Long-Term Credentials

## Description

IAM Roles provide temporary permissions to users, applications or AWS services.

They are safer than storing permanent credentials.

---

## Example

An EC2 instance needs access to S3:

```
EC2 Instance

↓

IAM Role

↓

S3 Bucket
```

The application receives temporary permissions without storing access keys.

---

# 6. Manage Permissions Carefully

## Description

IAM permissions should be reviewed regularly to ensure users only have the required access.

---

## Best Practices

- Remove unused permissions.
- Review IAM policies.
- Avoid excessive permissions.
- Use AWS managed policies when appropriate.

---

# 7. Secure AWS CLI Credentials

## Description

AWS CLI uses credentials to authenticate with AWS services.

These credentials must be protected.

---

## Best Practices

- Do not commit credentials to repositories.
- Use AWS profiles.
- Use environment variables when required.
- Use IAM Roles for applications.

---

# 8. Monitor Account Activity

## Description

Monitoring AWS activity helps detect suspicious actions and security problems.

---

## AWS Services

Examples:

- AWS CloudTrail for API activity logging.
- Amazon CloudWatch for monitoring resources.

---

# Key Takeaways

After completing this module, I understand:

✅ How to protect AWS accounts.

✅ Why MFA is important.

✅ How to apply least privilege.

✅ Why IAM Roles are preferred over permanent credentials.

✅ How to securely manage AWS CLI access.

✅ The importance of monitoring cloud environments.
