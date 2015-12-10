# AWS

1. Remove <root> account credential after downloading that credential.csv file.
2. 

Use groups to control access to resources, not users.

Virtual Private Cloud (VPC) is a logically isolated network in AWS cloud. It is the very first primary big subnet you have where you can create more smaller subnets to use.

## IAM - Identity and Access Management

Don't use root account!

Users, Groups, Roles, and Policies

Authenticate user, control access to resources and security.

### Group

If you have more users, you do not want to grant those users access to resources individually, that will be too tedious and time consuming. Instead we use a Group to cover all users with similar access rights and permissions.

In IAM, you cannot nest group.

Resource level traffic firewall.

Security group apply against resources.

### Roles

How is Roles different from Groups? When you want a user to "assume" a role. The user can switch role and once done with the things will switch back to their original role.

A user can be under one group but have many different roles.

More for EC2 user to access other AWS services like RDS database.

### Policies

Collection of permissions. You can apply policies to user, group, roles, etc. Policies are the foundation of it all.

### ACL

Source and protocol filtering. Subnet level traffic firewall. At the subnet level.

## S3 Bucket Policy vs IAM Policy

* [A very nice gem for file uploading](https://github.com/refile/refile)
* [10 useful CLI commands](http://cloudacademy.com/blog/aws-cli-10-useful-commands/)
* [AWS Signature Version 4](http://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-query-string-auth.html)

S3 is not a filesystem. It is a key-value store.

3 security settings for S3:

1. IAM policies
2. Bucket policies
3. ACLs - Legacy!
