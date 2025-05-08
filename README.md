Cloud-Based File Storage System

A secure, organized solution to store and share intern documents using AWS S3 and pre‑signed URLs.

Project Overview

This repository demonstrates how to:

Set up an AWS account

Create an S3 bucket

Organize storage with logical folders (prefixes)

Upload files with correct metadata

Configure and generate pre‑signed URLs for secure file access

These steps lay the foundation for a production‑ready file storage backend for internee.pk.

Prerequisites

AWS Account – Active AWS account with IAM user credentials.

AWS CLI or SDK – AWS CLI installed or AWS SDK (e.g., Boto3 for Python).

Permissions – IAM user with permissions to create buckets, upload objects, and generate pre‑signed URLs.

Step-by-Step Guide

1. Set Up an AWS Account

Navigate to AWS and sign up or log in.

Create or select an IAM user with programmatic access.

Generate and securely store Access Key ID and Secret Access Key.



2. Create an S3 Bucket

Open the AWS Management Console and go to S3.

Click Create bucket.

Choose a unique bucket name (e.g., intern-file-storage).

Select your AWS Region.

Leave public access blocked (for security).

Enable Versioning if you want object history and rollback.



3. Create Folders (Prefixes)

Inside your bucket, click Create folder three times:

joining-letters/

certificates/

reports/

These prefixes help group documents by type without true directories.



4. Upload Files

In the console or via SDK/CLI, upload files in binary mode:

Example CLI:

aws s3 cp resume.pdf s3://intern-file-storage/joining-letters/ --content-type application/pdf

Example Python (Boto3):

with open('doc.pdf', 'rb') as f:
    s3.upload_fileobj(f, 'intern-file-storage', 'reports/doc.pdf', ExtraArgs={'ContentType': 'application/pdf'})

Confirm the files appear under the correct prefixes.



5. Configure Bucket Permissions for Signed URLs

Ensure public access remains blocked at the bucket level.

Use your SDK to generate pre‑signed URLs that grant time‑limited access:

url = s3.generate_presigned_url(
    'get_object',
    Params={'Bucket': 'intern-file-storage', 'Key': 'reports/doc.pdf'},
    ExpiresIn=3600
)

Share the URL with users; it expires automatically after the specified duration.



Next Steps (Optional)

Implement a CLI or web interface to automate uploads and URL generation.

Enforce least‑privilege IAM policies.

Enable default encryption and logging for compliance.

Set up CORS, lifecycle rules, and Object Lock as needed.

© 2025 Internee.pk Intern Project
