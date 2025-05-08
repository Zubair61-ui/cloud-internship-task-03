# Cloud-Based File Storage System

A secure, organized solution to store and share intern documents using AWS S3 and pre‑signed URLs.

## Project Overview

This repository demonstrates how to:

### Set up an AWS account

### Create an S3 bucket

### Organize storage with logical folders (prefixes)

### Upload files with correct metadata

### Configure and generate pre‑signed URLs for secure file access

These steps lay the foundation for a production‑ready file storage backend for internee.pk.

## Prerequisites

### AWS Account – Active AWS account with IAM user credentials.

### Permissions – IAM user with permissions to create buckets, upload objects, and generate pre‑signed URLs.

## Step-by-Step Guide

### 1. Set Up an AWS Account

Navigate to AWS and sign up or log in.

Create or select an IAM user with programmatic access.

Generate and securely store Access Key ID and Secret Access Key.



### 2. Create an S3 Bucket

Open the AWS Management Console and go to S3.

Click Create bucket.

Choose a unique bucket name (e.g., intern-file-storage).

Select your AWS Region.

Leave public access blocked (for security).

Enable Versioning if you want object history and rollback.
[Create Bucket](create_bucket.png)


### 3. Create Folders (Prefixes)

Inside your bucket, click Create folder three times:

joining-letters/

certificates/

reports/

These prefixes help group documents by type without true directories.
[Created Folders](interns_folders.png)


### 4. Upload Files

In the AWS CLI, upload files in binary mode:

 ***CLI:***

aws s3 cp jhon-doe-joining-letter.pdf s3://intern-file-storage/joining-letters/ --content-type application/pdf
aws s3 cp jhon-doe-certificate.pdf s3://intern-file-storage/certificates/ --content-type application/pdf
aws s3 cp jhon-doe-joining-report.pdf s3://intern-file-storage/reports/ --content-type application/pdf

Confirm the files appear under the correct prefixes.



### 5. Configure Bucket Permissions for Signed URLs

Ensure public access remains blocked at the bucket level.

[Signed_url for pdf1](signed_url1.png). 

[Signed_url for pdf2](signed_url2.png).

[Signed_url for pdf3](signed_url3.png).  

Users can only access S3 object for 12 hours through pre-signed_urls.
Share the URL with users; it expires automatically after the specified duration.


### Final Output
[Access pdf through signed_url](access_url1.png)


© 2025 Internee.pk Intern Project
