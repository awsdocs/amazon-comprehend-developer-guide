# Tutorial: Analyzing Insights from Customer Reviews with Amazon Comprehend<a name="tutorial-reviews"></a>

This tutorial explains how to use Amazon Comprehend with [Amazon Simple Storage Service](https://aws.amazon.com/s3/), [AWS Glue](https://aws.amazon.com/glue/), [Amazon Athena](https://aws.amazon.com/athena/), and [Amazon QuickSight](https://aws.amazon.com/quicksight/) to gain valuable insights into your documents\. Amazon Comprehend can extract sentiment \(the mood of a document\) and entities \(names of people, organizations, events, dates, products, places, quantities, and titles\) from unstructured text\.

For example, you can get actionable insights from customer reviews\. In this tutorial, you analyze a sample dataset of customer reviews about a novel\. You use Amazon Comprehend sentiment analysis to determine whether customers feel positive or negative about the novel\. You also use Amazon Comprehend entities analysis to discover mentions of important entities, such as related novels or authors\. After following this tutorial, you might discover that over 50% of the reviews are positive\. You might also discover that customers are comparing authors and expressing interest in other classic novels\.

In this tutorial, you accomplish the following:
+ Store a sample dataset of reviews in [Amazon Simple Storage Service](https://aws.amazon.com/s3/) \(Amazon S3\)\. Amazon Simple Storage Service is an object storage service\.
+ Use [Amazon Comprehend](https://aws.amazon.com/comprehend/) to analyze the sentiment and entities in the review documents\.
+ Use an [AWS Glue](https://aws.amazon.com/glue/) crawler to store the results of the analysis in a database\. AWS Glue is an extract, transform, and load \(ETL\) service that lets you catalog and clean your data for analytics\.
+ Run [Amazon Athena](https://aws.amazon.com/athena/) queries to clean your data\. Amazon Athena is a serverless interactive query service\.
+ Create visualizations with your data in [Amazon QuickSight](https://aws.amazon.com/quicksight/)\. Amazon QuickSight is a serverless business intelligence tool for extracting insights from your data\.

The following diagram shows the workflow\.

![\[Workflow diagram of the procedures in the tutorial.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/tutorial-reviews-workflow.png)

**Estimated time to complete this tutorial:** 1 hour

**Estimated cost:** Some of the actions in this tutorial incur charges on your AWS account\. For information about the charges for each of these services, see the following pricing pages\.
+ [Amazon S3 pricing](https://aws.amazon.com/s3/pricing/)
+ [Amazon Comprehend pricing](https://aws.amazon.com/comprehend/pricing/)
+ [AWS Glue pricing](https://aws.amazon.com/glue/pricing/)
+ [Amazon Athena pricing](https://aws.amazon.com/athena/pricing/)
+ [Amazon QuickSight pricing](https://aws.amazon.com/quicksight/pricing/)

**Topics**
+ [Prerequisites](#tutorial-reviews-prereqs)
+ [Step 1: Adding Documents to Amazon S3](tutorial-reviews-add-docs.md)
+ [Step 2: \(CLI Only\) Creating an IAM Role for Amazon Comprehend](tutorial-reviews-create-role.md)
+ [Step 3: Running Analysis Jobs on Documents in Amazon S3](tutorial-reviews-analysis.md)
+ [Step 4: Preparing the Amazon Comprehend Output for Data Visualization](tutorial-reviews-tables.md)
+ [Step 5: Visualizing Amazon Comprehend Output in Amazon QuickSight](tutorial-reviews-visualize.md)

## Prerequisites<a name="tutorial-reviews-prereqs"></a>

To complete this tutorial, you need the following:
+ An AWS account\. If you don't have an AWS account, see the topic [Step 1: Set up an AWS Account and Create an Administrator User](https://docs.aws.amazon.com/comprehend/latest/dg/setting-up.html) in the *Amazon Comprehend User Guide* to set up a new account\.
+ An [AWS Identity and Access Management](https://aws.amazon.com/iam/) \(IAM\) user\. We highly recommend that you use an IAM user to protect your root account\. The root account has unrestricted access to AWS resources and billing information\. Using an IAM user with restricted permissions limits how much access you have within your account\. To learn how to set up an IAM user and group for your account, see the [Getting Started](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started.html) tutorial in the *IAM User Guide*\.
+ The following permissions policy attached to your IAM group or user\. The policy grants your IAM user some of the permissions required to complete this tutorial\. The next prerequisite describes the additional permissions you need\. 

  ```
  {
    "Version": "2012-10-17",
    "Statement":
    [
      {
        "Sid": "VisualEditor0",
        "Effect": "Allow",
        "Action":
        [
          "comprehend:*",
          "ds:AuthorizeApplication",
          "ds:CheckAlias",
          "ds:CreateAlias",
          "ds:CreateIdentityPoolDirectory",
          "ds:DeleteDirectory",
          "ds:DescribeDirectories",
          "ds:DescribeTrusts",
          "ds:UnauthorizeApplication",
          "iam:AttachRolePolicy",
          "iam:CreatePolicy",
          "iam:CreatePolicyVersion",
          "iam:CreateRole",
          "iam:DeletePolicyVersion",
          "iam:DeleteRole",
          "iam:DetachRolePolicy",
          "iam:GetPolicy",
          "iam:GetPolicyVersion",
          "iam:GetRole",
          "iam:ListAccountAliases",
          "iam:ListAttachedRolePolicies",
          "iam:ListEntitiesForPolicy",
          "iam:ListPolicies",
          "iam:ListPolicyVersions",
          "iam:ListRoles",
          "quicksight:*",
          "s3:*",
          "tag:GetResources"
        ],
        "Resource": "*"
      },
      {
        "Action":
        [
          "iam:PassRole"
        ],
        "Effect": "Allow",
        "Resource":
        [
          "arn:aws:iam::*:role/*Comprehend*"
        ]
      }
    ]
  }
  ```

  Use the previous policy to create an IAM policy and attach it to your group or user\. For information about creating an IAM policy, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) in the *IAM User Guide*\. For information about attaching an IAM policy, see [Adding and removing IAM identity permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *IAM User Guide*\.
+ Managed policies attached to your IAM group or user\. In addition to the previous policy, you must also attach the following AWS managed policies to your group or user:
  + `AWSGlueConsoleFullAccess`
  + `AWSQuicksightAthenaAccess`

  These managed policies give you permission to use AWS Glue, Amazon Athena, and Amazon QuickSight\. For information about attaching an IAM policy, see [Adding and removing IAM identity permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *IAM User Guide*\.