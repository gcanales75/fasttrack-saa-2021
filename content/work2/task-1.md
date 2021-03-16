+++ 
title = "Tasks" 
chapter = false 
weight = 1 
+++

### Task 1: Configure a *resource based policy*

1. Log in as the admin user of your AWS account

1. Go to Services *search box* > S3

1. Click on the bucket you will use for this demo

1. Click on the **Permissions** tab

1. Scroll down to the **Bucket policy** section

1. Click **Edit**

1. Paste the below policy in the *policy box*

    ```JSON
    {
        "Version": "2012-10-17",
        "Id": "S3",
        "Statement": [
            {
                "Sid": "editBucket",
                "Effect": "Allow",
                "Principal": {
                    "AWS": "arn:aws:iam::[ACCOUNT_NUMBER]:user/demo-user-1"
                },
                "Action": [
                    "s3:DeleteObject",
                    "s3:GetObject",
                    "s3:PutObject"
                ],
                "Resource": "arn:aws:s3:::[DEMO_BUCKET]/*"
            }
        ]
    }
    ````

	{{% notice note %}}
NOTE 1: Edit the `[ACCOUNT_NUMBER]` value paramenter in the `Principal.AWS` key, inside the *Statement*
{{% /notice %}}

	{{% notice note %}}
NOTE 2: Edit the `[DEMO_BUCKET]` value paramenter in the `Resource` key, inside the *Statement*
{{% /notice %}}

1. Log out and log back in as `demo-user-1`

1. Go to Services *search box* > S3

1. Access the S3 bucket used for this demo

1. Upload, download and delete objects into the S3 bucket

	{{% notice tip %}}
Mention that this actions can be executed based on the *resource based policy* attached to the bucket, regardless the user `demo-user-1` do not have any IAM policy allowing this actions.
{{% /notice %}}

**DEMO 2 END**