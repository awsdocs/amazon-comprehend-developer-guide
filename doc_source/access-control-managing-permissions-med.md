# Using Identity\-Based Policies \(IAM Policies\) for Amazon Comprehend Medical<a name="access-control-managing-permissions-med"></a>

This topic shows example identity\-based policies\. The examples show how an account administrator can attach permissions policies to IAM identities\. This enables users, groups, and roles to perform Amazon Comprehend Medical actions\. 

**Important**  
To understand permissions, we recommend [Overview of Managing Access Permissions to Amazon Comprehend Medical Resources](access-control-overview-med.md)\. 

This example policy is required to use the Amazon Comprehend Medical document analysis actions\.

```
{
   "Version": "2012-10-17",
   "Statement": [{
      "Sid": "AllowDetectActions",
      "Effect": "Allow",
      "Action": [
                "comprehendmedical:DetectEntitiesV2",
                "comprehendmedical:DetectEntities",
                "comprehendmedical:DetectPHI",
                
                "comprehendmedical:StartEntitiesDetectionV2Job",
                "comprehendmedical:ListEntitiesDetectionV2Jobs",
                "comprehendmedical:DescribeEntitiesDetectionV2Job",
                "comprehendmedical:StopEntitiesDetectionV2Job",

                "comprehendmedical:StartPHIDtectionJob",
                "comprehendmedical:ListPHIDetectionJobs",
                "comprehendmedical:DescribePHIDetectionJob",
                "comprehendmedical:StopPHIDetectionJob",
                
                "comprehendmedical:InferRxNorm",
                "comprehendmedical:InferICD10CM",
             ],   
      "Resource": "*"
      }
   ]
}
```

The policy has one statement that grants permission to use the `DetectEntities` and `DetectPHI` actions\. 

The policy doesn't specify the `Principal` element because you don't specify the principal who gets the permission in an identity\-based policy\. When you attach a policy to a user, the user is the implicit principal\. When you attach a policy to an IAM role, the principal identified in the role's trust policy gets the permission\. 

To see all the Amazon Comprehend Medical API actions and the resources that they apply to, see [Amazon Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref-med.md)\.

## Permissions Required to Use the Amazon Comprehend Medical Console<a name="auth-console-permissions-med"></a>

The permissions reference table lists the Amazon Comprehend Medical API operations and shows the required permissions for each operation\. For more information, about Amazon Comprehend Medical API permissions, see [Amazon Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref-med.md)\.

To use the Amazon Comprehend Medical console, grant permissions for the actions shown in the following policy\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "comprehendmedical:*",
                "iam:ListRoles",
                "iam:GetRole",
                "s3:ListAllMyBuckets",
                "s3:ListBucket",
                "s3:GetBucketLocation"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

The Amazon Comprehend Medical console needs these permissions for the following reasons:
+ `iam` permissions to list the available IAM roles for your account\.
+ `s3` permissions to access the Amazon S3 buckets and objects that contain the data\.

When you create an asynchronous batch job using the console, you can also create an IAM role for your job\. To create an IAM role using the console, users must be granted the additional permissions shown here to create IAM roles and policies, and to attach policies to roles\.

```
{
  "Version": "2012-10-17",
  "Statement": [
      {
         "Action": [
            "iam:CreateRole",
            "iam:CreatePolicy",
            "iam:AttachRolePolicy",
            "iam:PassRole"
         ],
         "Effect": "Allow",
         "Resource": "*"
      }
   ]
}
```

The Amazon Comprehend Medical console needs these permissions to create roles and policies and to attach roles and policies\. The `iam:PassRole` action enables the console to pass the role to Amazon Comprehend Medical\.

## AWS Managed \(Predefined\) Policies for Amazon Comprehend Medical<a name="access-policy-aws-managed-policies-med"></a>

AWS addresses many common use cases by providing standalone IAM policies that are created and administered by AWS\. These AWS managed policies grant necessary permissions for common use cases so that you can avoid having to investigate what permissions are needed\. For more information, see [AWS Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\. 

The following AWS managed policy, which you can attach to users in your account, is specific to Amazon Comprehend Medical\.
+ **ComprehendMedicalFullAccess** – Grants full access to Amazon Comprehend Medical resources\. Includes permission to list and get IAM roles\.

You must apply the following additional policy to any user using Amazon Comprehend Medical:

```
{
  "Version": "2012-10-17",
  "Statement": [
      {
         "Action": [
            "iam:PassRole"
         ],
         "Effect": "Allow",
         "Resource": "*"
      }
   ]
}
```

You can review the managed permissions policies by signing in to the IAM console and searching for specific policies there\.

These policies work when you are using AWS SDKs or the AWS CLI\.

You can also create your own IAM policies to allow permissions for Amazon Comprehend Medical actions and resources\. You can attach these custom policies to the IAM users or groups that require them\. 

## Role\-Based Permissions Required for Asynchronous Operations<a name="auth-role-permissions-med"></a>

To use the Amazon Comprehend Medical asynchronous operations, grant Amazon Comprehend Medical access to the Amazon S3 bucket that contains your document collection\. Do this by creating a data access role in your account to trust the Amazon Comprehend Medical service principal\. For more information about creating a role, see [Creating a Role to Delegate Permissions to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *AWS Identity and Access Management User Guide*\. 

The following is the role's trust policy\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "comprehendmedical.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

After you have created the role, create an access policy for it\. The policy should grant the Amazon S3 `GetObject` and `ListBucket` permissions to the Amazon S3 bucket that contains your input data\. It also grants permissions for the Amazon S3 `PutObject` to your Amazon S3 output data bucket\. 

The following example access policy contains those permissions\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::input bucket/*"
            ],
            "Effect": "Allow"
        },
        {
            "Action": [
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::input bucket"
            ],
            "Effect": "Allow"
        },
        {
            "Action": [
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::output bucket/*"
            ],
            "Effect": "Allow"
        }
    ]
}
```

## Customer Managed Policy Examples<a name="access-policy-customer-managed-examples-med"></a>

In this section, you can find example user policies that grant permissions for various Amazon Comprehend Medical actions\. These policies work when you are using AWS SDKs or the AWS CLI\. When you are using the console, you must grant permissions to all the Amazon Comprehend Medical APIs\. This is discussed in [Permissions Required to Use the Amazon Comprehend Medical Console](#auth-console-permissions-med)\.

**Note**  
All examples use the us\-east\-2 Region and contain fictitious account IDs\.

**Examples**  

### Example 1: Allow All Amazon Comprehend Medical Actions<a name="custom-policy-1-med"></a>

After you sign up for AWS, you create an administrator to manage your account, including creating users and managing their permissions\. 

You can choose to create a user who has permissions for all Amazon Comprehend actions\. Think of this user as a service\-specific administrator for working with Amazon Comprehend\. You can attach the following permissions policy to this user\.

```
{
   "Version": "2012-10-17",
   "Statement": [{
      "Sid": "AllowAllComprehendMedicalActions",
      "Effect": "Allow",
      "Action": [
         "comprehendmedical:*"],
      "Resource": "*"
      }
   ]
}
```

### Example 2: Allow Only DetectEntities Actions<a name="custom-policy-2-med"></a>

The following permissions policy grants user permissions to detect entities in Amazon Comprehend Medical, but not to detect PHI operations\.

```
{
   "Version": "2012-10-17",
   "Statement": [{
      "Sid": "AllowDetectEntityActions",
      "Effect": "Allow",
      "Action": [
                "comprehendedical:DetectEntities"
             ],   
            "Resource": "*"
            ]
        }
    ]
}
```