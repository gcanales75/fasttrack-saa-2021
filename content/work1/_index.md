+++
title = "Demo 1 - Create IAM User & Policies"
date = 2021-02-17T17:04:42-06:00
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

### Description

In this demo you will demostrate how to create custom IAM policies and users and put those policies to the test

#### Demo diagram

<img src="images/IAM-demo-1.png" alt="drawing" width="800"/>

1. In this Demo you will create the following resources

    * 2x  *Customer manged* IAM policies

    * 1x IAM user

1. Attach 4 policies to an IAM user

1. Perform the following actions:

    * Test if the IAM user is able to stop, reboot or terminate a *Production* environment EC2 instance
    * Put an item in a DynamoDB table

### Pre-requisites

1. At least one EC2 instance running, with added Tags

	| Tag Key | Tag Value  |
	|---|---|
	| Env | Production |

1. At least two DynamoDB tables, one called `demo-iam-table`

    You can create table `demo-iam-table` with this cli command:

    ````bash
    aws dynamodb create-table --table-name demo-iam-table --key-schema --attribute-definitions AttributeName=email,AttributeType=S --key-schema AttributeName=recordId,KeyType=HASH --billing-mode PAY_PER_REQUEST
    ````