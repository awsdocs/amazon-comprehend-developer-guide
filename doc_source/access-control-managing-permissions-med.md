# Using Identity\-Based Policies \(IAM Policies\) for Comprehend Medical<a name="access-control-managing-permissions-med"></a>

This topic provides examples of identity\-based policies that demonstrate how an account administrator can attach permissions policies to IAM identities \(that is, users, groups, and roles\) and thereby grant permissions to perform Comprehend Medical actions\. 

**Important**  
Before you proceed, we recommend that you review [Overview of Managing Access Permissions to Comprehend Medical Resources](access-control-overview-med.md)\. 

The following is the permissions policy required to use the Comprehend Medical document analysis actions:

```
{
   "Version": "2012-10-17",
   "Statement": [{
      "Sid": "AllowDetectActions",
      "Effect": "Allow",
      "Action": [
                "comprehendmedical:DetectEntities",
                "comprehendmedical:DetectPHI"
             ],   
      "Resource": "*"
      }
   ]
}
```

The policy has one statement that grants permission to use the `DetectEntities` and `DetectPHI` actions\. 

The policy doesn't specify the `Principal` element because you don't specify the principal who gets the permission in an identity\-based policy\. When you attach a policy to a user, the user is the implicit principal\. When you attach a permissions policy to an IAM role, the principal identified in the role's trust policy gets the permissions\. 

For a table showing all of the Comprehend Medical API actions and the resources that they apply to, see [Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref-med.md)\.

## Permissions Required to Use the Comprehend Medical Console<a name="auth-console-permissions-med"></a>

The permissions reference table lists the Comprehend Medical API operations and shows the required permissions for each operation\. For more information, about Comprehend Medical API permissions, see [Comprehend Medical API Permissions: Actions, Resources, and Conditions Reference](comprehend-api-permissions-ref-med.md)\.

To use the Comprehend Medical console, you need to grant permissions for the actions shown in the following policy: 

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

The Comprehend Medical console needs these additional permissions for the following reasons:
+ `iam` permissions to list the available IAM roles for your account\.
+ `s3` permissions to access the Amazon S3 buckets and objects that contain the data for topic modeling\.

When you create an asynchronous batch job or a topic modeling job using the console, you have the option to have the console create an IAM role for your job\. To create an IAM role, users must be granted the following additional permissions to create IAM roles and policies, and to attach policies to roles:

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

The Comprehend Medical console needs these additional permissions for the following reasons:
+ `iam` permissions to create roles and policies and to attach roles and policies\. The `iam:PassRole` action enables the console to pass the role to Comprehend Medical\.

## AWS Managed \(Predefined\) Policies for Comprehend Medical<a name="access-policy-aws-managed-policies-med"></a>

AWS addresses many common use cases by providing standalone IAM policies that are created and administered by AWS\. These AWS managed policies grant necessary permissions for common use cases so that you can avoid having to investigate what permissions are needed\. For more information, see [AWS Managed Policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\. 

The following AWS managed policy, which you can attach to users in your account, are specific to Comprehend Medical:
+ **ComprehendMedicalFullAccess** – Grants full access to Comprehend Medical resources\. Includes permission to list and get IAM roles\.

You need to apply the following additional policy to any user that will use Comprehend Medical:

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

You can also create your own custom IAM policies to allow permissions for Comprehend Medical actions and resources\. You can attach these custom policies to the IAM users or groups that require those permissions\. 

## Role\-Based Permissions Required for Asynchronous Operations<a name="auth-role-permissions-med"></a>

To use the Comprehend Medical asynchronous operations, you must grant Comprehend Medical access to the Amazon S3 bucket that contains your document collection\. You do this by creating a data access role in your account to trust the Comprehend Medical service principal\. For more information about creating a role, see [Creating a Role to Delegate Permissions to an AWS Service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *AWS Identity and Access Management User Guide*\. 

The following is the role's trust policy:

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "com.amazonaws.deepinsight.medical"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

After you have created the role, you must create an access policy for that role\. The should grant the Amazon S3 `GetObject` and `ListBucket` permissions to the Amazon S3 bucket that contains your input data, and the Amazon S3 `PutObject` permission to your Amazon S3 output data bucket\. 

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

In this section, you can find example user policies that grant permissions for various Comprehend Medical actions\. These policies work when you are using AWS SDKs or the AWS CLI\. When you are using the console, you need to grant permissions to all the Comprehend Medical APIs\. This is discussed in [Permissions Required to Use the Comprehend Medical Console](#auth-console-permissions-med)\.

**Note**  
All examples use the us\-east\-2 region and contain fictitious account IDs\.

**Examples**  

### Example 1: Allow All Comprehend Medical Actions<a name="custom-policy-1-med"></a>

After you sign up for AWS, you create an administrator user to manage your account, including creating users and managing their permissions\. 

You might choose to create a user who has permissions for all Amazon Comprehend actions \(think of this user as a service\-specific administrator\) for working with Amazon Comprehend\. You can attach the following permissions policy to this user\.

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

The following permissions policy grants user permissions to detect entities in Comprehend Medical, but not to detect PHI operations\.

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