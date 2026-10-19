# Introduction to AWS IAM — Users, Groups, Policies, and Permission Testing

Hands-on Qwiklabs lab from my UMGC coursework (CCA 630) covering the core of AWS identity management — including verifying that permissions actually deny what they should.

## What I built
- **IAM users**: user-1, user-2, user-3 (plus the student account), with console passwords and security-credential review (access keys, MFA status)
- **User groups with role-based permissions**:
  - **EC2-Admin** — custom inline JSON policy: `ec2:Describe*`, `ec2:StartInstances`, `ec2:StopInstances`, `cloudwatch:DescribeAlarms`
  - **EC2-Support** — AWS managed policy **AmazonEC2ReadOnlyAccess** (reviewed the policy JSON: ec2:Describe*, elasticloadbalancing:Describe*)
  - **S3-Support** — AWS managed policy **AmazonS3ReadOnlyAccess** (s3:Get*, s3:List*)
  - **QLReadOnly**
- Added users to groups and confirmed group membership counts updated

## Permission verification (the important part)
I signed in as each restricted user and tested the boundaries:
- A user with no EC2 permissions received **"You are not authorized to perform this operation"** in the EC2 console
- An S3-scoped user was denied **s3:ListAllMyBuckets**
- An EC2-Support user could view the running instance (t3.micro, status checks passed) and work through instance state actions only within their policy scope
- Reviewed the IAM dashboard: users, groups, roles, policies, and the root-account MFA security recommendation

## Skills demonstrated
- AWS IAM users, groups, and group-based permission management
- AWS managed policies vs. custom inline JSON policies
- Least-privilege verification through negative testing


---
*Shannon Javone Jenkins — MS in Cloud Computing Architecture, University of Maryland Global Campus (UMGC). Graduate coursework and hands-on labs.*
