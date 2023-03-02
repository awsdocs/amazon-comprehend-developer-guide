# IAM policies and permissions<a name="flywheels-permissions"></a>

You configure the following policies and permissions to use flywheels: 
+ [Configure IAM user permissions](#flywheels-permissions-iam) for users to access flywheel operations\.
+ \(Optional\) [Configure permissions for AWS KMS keys](#flywheels-permissions-kms) for the data lake\.
+ [Create a data access role](#flywheels-permissions-service) that authorizes Amazon Comprehend to access the data lake\.

## Configure IAM user permissions<a name="flywheels-permissions-iam"></a>

To use flywheel capabilities, add appropriate permissions policies to your AWS Identity and Access Management \(IAM\) identities \(users, groups, and roles\)\. 

The following example shows permissions policy to create datasets, to create and manage flywheels, and to run the flywheel\.

**Example IAM policy to manage flywheels**  

```
{
  "Effect": "Allow",
  "Action": [
    "comprehend:CreateFlywheel",
    "comprehend:DeleteFlywheel",
    "comprehend:UpdateFlywheel",
    "comprehend:ListFlywheels",
    "comprehend:DescribeFlywheel",
    "comprehend:CreateDataset",
    "comprehend:DescribeDataset",
    "comprehend:ListDatasets",
    "comprehend:StartFlywheelIteration",
    "comprehend:DescribeFlywheelIteration",
    "comprehend:ListFlywheelIterationHistory"    
  ],
  "Resource": "*"
}
```

For information about creating IAM policies for Amazon Comprehend, see [How Amazon Comprehend works with IAM](security_iam_service-with-iam.md)\. 

## Configure permissions for AWS KMS keys<a name="flywheels-permissions-kms"></a>

If you are using AWS KMS keys for your data in the data lake, set up the required permissions\. For information, see [Permissions required to use KMS encryption](security_iam_id-based-policy-examples.md#auth-kms-permissions) \.

## Create a data access role<a name="flywheels-permissions-service"></a>

You create a data access role in IAM for Amazon Comprehend to access flywheel data in the data lake\. If you use the console to create a flywheel, the system can optionally create a new role for this purpose\. For more information, see [Role\-based permissions required for asynchronous operations](security_iam_id-based-policy-examples.md#auth-role-permissions)\.