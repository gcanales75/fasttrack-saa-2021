+++ 
title = "Tasks" 
chapter = false 
weight = 1 
+++

### Task 1: Create Customer Managed Policies

1. First, you will create the **EC2** deny actions policy (Stop, Terminate and Reboot)

1. Login to the IAM Console

1. Go to Policies -> **Create policy**

1. This policy will be created using the *Visual editor*

1. Click on **Choose a service**

1. Click on **EC2** or type **EC2** in the *search box*

1. Click on **Switch to deny permissions**

1. Under **Access level**, expand the **Write** options

1. Look for the following actions and mark their checkboxes

    * TerminateInstances
    * StopInstances
    * RebootInstances

1. Click on the **Resources** section

1. Select **All resources**

1. Click on **Request conditions**

1. Click on **Add condition**

1. You will be prompted an **Add request condition** window, in **Condition key** select **ec2:ResourceTag**

1. In **TagKey** type: `Env`

1. In **Operator** select **StringEquals**

1. In **Value** type: `Production`

1. Click on **Add**

1. Click on **Next: Tags**

1. Click on **Next: Review**

1. Add a name to this policy (e.g. "ec2-deny-policy")

1. Click on **Create Policy**

1. Now you will create the **DynamoDB** allow policy (PutItem, DeleteItem)

1. Go to Policies -> Create policy

1. This policy will be created using the *Visual editor*

1. Click on **Choose a service**

1. Click on **DynamoDB** or type **DynamoDB** in the *search box*

1. Under **Access level**, expand the **Write** options

1. Look for the following actions and mark their checkboxes

    * PutItem
    * DeleteItem

1. Click on the **Resources** section

1. You will set an specific *table* on which this policy will apply. You will set the table created in the lab pre-requisites. Click on **Add ARN**

1. Click on the checkbox to select *Any* region

1. In table name type `demo-iam-table`

1. Click on **Add**

1. Click on **Next: Tags**

1. Click on **Next: Review**

1. Add a name to this policy (e.g. "dynamodb-put-delete-policy")

1. Click on **Create Policy**

### Task 2: Create IAM User

1. From the left pane, click on **Users**

1. Click on **Add user**

1. In **User name**, type `demo-user-1`

1. Under **Select AWS access type**, mark the checkbox next to **AWS Management Console access**

1. For ease of the lab, we'll use a *custom password*, in **Console password** select **Custom password**

1. Type a *strong* password (e.g. "myIamUser$trongP@ssw0rd")

1. Uncheck **User must create a new password at next sign-in** option

1. Click on **Next: Permissions**

1. Under **Set permissions** click on **Attach existing policies directly**

1. In the **Policies** *search box* type the *Customer managed* policies and then the *AWS managed* policies. Click on each policy to add them

    Customer managed
    * ec2-deny-policy
    * dynamodb-put-delete-policy

    AWS managed

    * AmazonEC2FullAccess
    * ReadOnlyAccess (you will find many policies with "ReadOnlyAccess" as suffix, scroll down to find that specific policy)

1. Once finished adding the 4 policies, click on **Next: Tags**

1. Click on **Next: Review**

1. Verify the 4 policies are being added and click on **Create user**

1. Click on **Close**

1. You can click on the IAM user recently created aand review the JSON document policies.

### Task 3: Test IAM Policies

1. Log out and log back in as `demo-user-1`

1. Navigate in the **AWS console** and try to perform some actions

1. Go to **EC2** service and try to Stop, Terminate or Reboot the instance with the *Production* environment Tag. Actions will be denied

1. Go to **DynamoDB** and try to put an item in table `demo-iam-table`, action should be allowed. If you have another **DynamoDB** table try to manually put an item, action should be denied.

**DEMO 1 END**