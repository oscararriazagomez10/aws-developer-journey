# AWS Command Line Interface (AWS CLI)

## Overview

The AWS Command Line Interface (AWS CLI) is a tool that allows to interact with AWS servervices directly from the terminal.

Instead of using the AWS Management Console, developers and system administrators can execute commands to create, manage and monitor AWS resources.

---

## Why use AWS CLI?

AWS CLI is widely used because it allows:

- Faster management of AWS resources.
- Task automation.
- Script Integration.
- Infrastructure management from the command Line.
- Better productivity for developers.

---
## Official Resources 

- AWS CLI Documentation:
  https://docs.aws.amazon.com/cli/

- AWS CLI Download:
  https://docs.aws.amazon.com/es_es/cli/latest/userguide/getting-started-install.html.

- AWS CLI Command Reference
  https://docs.aws.amazon.com/cli/latest/reference/

## Installation

AWS CLI can be installed on windows, macOs and Linux.

After installation, verify that it is working correctly:

```bash
aws --version
```
---

## Configuration

Configure AWS CLI with:

```bash
aws configure
```

The command requests:

- AWS Access Key ID
- AWS Secret Access Key
- Default region
- Output Format

Example:

```text
AWS Access Key ID: ****************
AWS Secret Access Key: ****************
Default region: eu-west-1
Default output format: json
```
---

## Common Commands 

### Check AWS CLI version

```bash
aws --version
```
---

### Check the current identity

```bash
aws sts get-caller-identity
```

This command verifies that AWS CLI is correctly configured.

---

### List IAM users

```bash
aws iam list-users
```
---

### List S3 buckets

```bash
aws s3 ls
```


---


## Best Practices

- Never share your Access Keys.
- Rotate credentials regularly.
- Use IAM Users instead of the Root account.
- Enable MFA whenever possible.
- Follow the Principle of Least Privilege.

---

## Key Takeaways 

After completing this section, I am able to:

- Install AWS CLI
- Configure AWS CLI.
- Connect securely to an AWS account.
- Execute basis AWS Commands.
- Manage AWS resources from the terminal.




