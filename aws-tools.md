# AWS Development

## Getting Started with AWS Development

### 0. Get an AWS Account

- set up User Accounts; Follow [IAM Best Practices](http://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html?icmpid=docs_iam_console) 

- Set up 

### 1. Install Python SDK

`pip install boto3`

2. [Install & Configure](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html) Command Line Interface (CLI)

- Install CLI

`pip install awscli`

Once installed check the version:

```
(awsdev) AKs-MacBook-Pro:~ ak$ aws --version
aws-cli/1.11.19 Python/2.7.10 Darwin/16.1.0 botocore/1.4.76
```

- Configure CLI

```
$ aws configure
AWS Access Key ID [None]: AKIAIOSFODNN7EXAMPLE
AWS Secret Access Key [None]: wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
Default region name [None]: us-west-2
Default output format [None]: ENTER
```

2. Working with the AWS Storage (S3)

- List S3 buckets

`aws s3 ls`
(if permission is granted for the CLI user then the S3 listing is shown)

- Copying files

see [acl](http://docs.aws.amazon.com/AmazonS3/latest/dev/acl-overview.html#canned-acl) for info on seeting right access control on the copied files.
```
(awsdev) AKs-MacBook-Pro:s3 ak$ echo "three lines" >> testfile.txt 
(awsdev) AKs-MacBook-Pro:s3 ak$ aws s3 cp testfile.txt s3://aktestdocs/all/testfile.txt --acl public-read
upload: ./testfile.txt to s3://aktestdocs/all/testfile.txt
(awsdev) AKs-MacBook-Pro:s3 ak$ 
```

Resources:
- <http://cloudacademy.com/blog/aws-cli-10-useful-commands/>


----
_last updated by @akaak in Nov 2016_
