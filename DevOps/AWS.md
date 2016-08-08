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

* [Best Rails image uploader](https://infinum.co/the-capsized-eight/articles/best-rails-image-uploader-paperclip-carrierwave-refile)
* [AWS Ruby Blog](https://ruby.awsblog.com/)
* [Downloading Objects from S3 using AWS SDK for Ruby](https://ruby.awsblog.com/post/Tx354Y6VTZ421PJ/Downloading-Objects-from-Amazon-S3-using-the-AWS-SDK-for-Ruby)
* [A very nice gem for file uploading](https://github.com/refile/refile)
* [10 useful CLI commands](http://cloudacademy.com/blog/aws-cli-10-useful-commands/)
* [AWS Signature Version 4](http://docs.aws.amazon.com/AmazonS3/latest/API/sigv4-query-string-auth.html)
* [Signing CloudFront URLs for serving private content](https://github.com/dylanvaughn/aws_cf_signer)

S3 is not a filesystem. It is a key-value store.

3 security settings for S3:

1. IAM policies
2. Bucket policies
3. ACLs - Legacy!

## Choose your object name (key) carefully

* [**Request Rate and Performance Considerations**](http://docs.aws.amazon.com/AmazonS3/latest/dev/request-rate-perf-considerations.html)
* [Amazon S3 Performance Tips & Tricks](https://aws.amazon.com/blogs/aws/amazon-s3-performance-tips-tricks-seattle-hiring-event/)

The object names you choose actually dictate how S3 manage the keymap.

Keys are all represented in S3 as strings like this:

```
bucketname/keyname
```

Keys in S3 are **partitioned by prefix**. S3 has automation that continually looks for areas of the keyspace that need splitting. Partitions are split either due to sustained high request rates, or because they contain a large number of keys (which would slow down lookups within the partition).

Smart naming of keys can have performance implications. But only if you have more than 100 request/second.

```
// Bad
examplebucket/2013-26-05-15-00-00/cust1234234/photo1.jpg
examplebucket/2013-26-05-15-00-00/cust3857422/photo2.jpg
examplebucket/2013-26-05-15-00-00/cust1248473/photo2.jpg

// Good
examplebucket/232a-2013-26-05-15-00-00/cust1234234/photo1.jpg
examplebucket/7b54-2013-26-05-15-00-00/cust3857422/photo2.jpg
examplebucket/921c-2013-26-05-15-00-00/cust1248473/photo2.jpg
```

For non-CDN objects, you want to introduce randomness in order not to overwhelm the **single index partition**.

**Note:**

For Jobline avatar or any assets to be downloaded by client, using Amazon CloudFront CDN is a much better option. It will reduce cost also since it send fewer requests directly to S3.


## s3cmd and aws-cli

```
▶ brew install s3cmd
▶ brew install python
▶ pip install awscli
▶ aws configure

▶ aws s3 ls s3://jobline-assets/avatars/ | wc -l
▶ aws s3 ls --recursive s3://jobline-assets/claims/ | wc -l
▶ aws s3 ls --recursive s3://jobline-assets/timesheets/ | wc -l

// Last check count Feb 15, 2016
39411
10923
5335
```