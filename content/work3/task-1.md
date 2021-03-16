+++ 
title = "Tasks" 
chapter = false 
weight = 1 
+++

### Task 1: Create the Assume role IAM Policy in Account A

1. Login to account **A** as an admin

1. Go to Services *search box* > IAM

1. Go to Policies -> **Create policy**

1. This policy will be created using the *Visual editor*

1. Click on **Choose a service**

1. Click on **STS** or type **STS** in the *search box*

1. Under **Access level**, expand the **Write** options

1. Mark the checkbox next to **AssumeRole**

1. Click on the **Resources** section

1. You will set an specific *role* in Account **B** to be assumed. Click on **Add ARN**

1. In **Account** type the Account **B** number

1. In **Role name with path** type `demo-role-sqs` (this role will be created later)

1. Click on **Add**

1. Click on **Next: Tags**

1. Click on **Next: Review**

1. Add a name to this policy (e.g. `demo-cross-account-policy`)

1. Click on **Create Policy**

### Task 2: Create IAM user which will have attached the policy created in Task 1

1. From the left pane, click on **Users**

1. Click on **Add user**

1. In **User name**, type `demo-cross-account-user`

1. Under **Select AWS access type**, mark the checkbox next to **AWS Management Console access**

1. For ease of the lab, we'll use a *custom password*, in **Console password** select **Custom password**

1. Type a *strong* password (e.g. "myIamUser$trongP@ssw0rd")

1. Uncheck **User must create a new password at next sign-in** option

1. Click on **Next: Permissions**

1. Under **Set permissions** click on **Attach existing policies directly**

1. In the **Policies** *search box* type `demo-cross-account-policy` and mark the checkbox

1. Click on **Next: Tags**

1. Click on **Next: Review**

1. Verify the policy has being added and click on **Create user**

1. Click on **Close**

### Task 2: Create IAM role in account B

1. Login to account **B** as an admin

1. Go to Services *search box* > IAM

1. From the left pane, click on **Roles**

1. Click on **Create role**

1. Under **Select type of trusted entity**, click on **Another AWS account**

1. Under **Specify accounts that can use this role**, for **Account ID** type the Account **A** number

1. Click **Next: Permissions**

1. Under **Attach permissions policies**, use the **Policies** *search box* to find and add these two **AWS Managed** policies:

	* ReadOnlyAccess 
	* AmazonSQSFullAccess

1. Click on **Next: Tags**

1. Click on **Next: Review**

1. In **Role name** type: `demo-role-sqs`

1. Click **Create role**

### Task 3: Log in as demo-cross-account-user

1. Login as `demo-cross-account-user` in account A

	{{% notice tip %}}
Try to navigate into a couple of services (e.g. EC2, S3) to demostrate that this user has no admin nor read-only access to any AWS service
{{% /notice %}}

1. From the upper right of your AWS console, click on `demo-cross-account-user @ [ACCOUNT_NUMBER]` to display the options and click on **Switch roles**

1. Click on **Switch role**

1. In **Account** type your account **B** number

1. In **Role** type `demo-role-sqs`

1. In **Display Name** type `demo-switch-role`

1. Click on **Switch Role**

	{{% notice tip %}}
Now you are logged in the Account **B** as an account **A** user. Click on `demo-switch-role` at the upper right corner to show accounts, user logged and role used
{{% /notice %}}

1. Go to Services *search box* > SQS

1. Create an SQS

#### END DEMO 3