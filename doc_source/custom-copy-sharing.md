# Sharing a custom model with another AWS account<a name="custom-copy-sharing"></a>

With Amazon Comprehend, you can share your custom models with others, so they can import your models into their AWS accounts\. When a user imports one of your custom models, they create a new custom model in their account\. Their new model duplicates the one that you shared\.

To share a custom model, you attach a policy to it that authorizes others to import it\. Then, you provide those users with the details that they need\.

**Note**  
When other users import a custom model that you've shared, they must use the same AWS Region —for example, US East \(N\. Virginia\)— that contains your model\.

**Topics**
+ [Before you begin](#custom-copy-sharing-prerequisites)
+ [Resource\-based policies for custom models](#custom-copy-sharing-example-policy)
+ [Step 1: Add a resource\-based policy to a custom model](#custom-copy-sharing-adding-policy)
+ [Step 2: Provide the details that others need to import](#custom-copy-sharing-details)

## Before you begin<a name="custom-copy-sharing-prerequisites"></a>

Before you can share a model, you must have a trained custom classifier or custom entity recognizer in Amazon Comprehend in your AWS account\. For more information about training custom models, see [Custom classification](how-document-classification.md) or [Custom entity recognition](custom-entity-recognition.md)\.

### Required permissions<a name="custom-copy-sharing-prerequisites-permissions"></a>

#### IAM policy statement<a name="custom-copy-sharing-prerequisites-permissions-iam"></a>

Before you can add a resource\-based policy to a custom model, you require permissions in AWS Identity and Access Management \(IAM\)\. Your user, group, or role must have a policy attached so you can create, get, and delete model policies, as shown in the following example\.

**Example IAM policy to manage resource\-based policies for custom models**  

```
{
  "Effect": "Allow",
  "Action": [
    "comprehend:PutResourcePolicy",
    "comprehend:DeleteResourcePolicy",
    "comprehend:DescribeResourcePolicy"
  ],
  "Resource": "arn:aws:comprehend:us-west-2:111122223333:document-classifier/foo/version/*"
}
```

For information about creating an IAM policy, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) in the *IAM User Guide*\. For information about attaching an IAM policy, see [Adding and removing IAM identity permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *IAM User Guide*\.

#### AWS KMS key policy statement<a name="custom-copy-sharing-prerequisites-permissions-kms"></a>

If you are sharing an encrypted model, then you might need to add permissions for AWS KMS\. This requirement depends on the type of KMS key that you use to encrypt the model in Amazon Comprehend\. 

An **AWS owned key** is owned and managed by an AWS service\. If you use an AWS owned key, you do not need to add permissions for AWS KMS, and you can skip this section\.

A **Customer managed key** is a key that you create, own, and manage in your AWS account\. If you use a customer managed key, you must add a statement to your KMS key policy\. 

The policy statement authorizes one or more entities \(such as users or accounts\) to perform the AWS KMS operations required to decrypt the model\. 

You use condition keys to help prevent the confused deputy problem\. For more information, see [Cross\-service confused deputy prevention](cross-service-confused-deputy-prevention.md)\.

Use the following condition keys in the policy to validate the entities that access your KMS key\. When a user imports the model, AWS KMS checks that the ARN of the source model version matches the condition\. If you do not include a condition in the policy, the specified principals can use your KMS key to decrypt any model version:
+ [aws:SourceArn](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html#condition-keys-sourcearn) – Use this condition key with the `kms:GenerateDataKey` and `kms:Decrypt` actions\.
+ [kms:EncryptionContext](https://docs.aws.amazon.com/kms/latest/developerguide/policy-conditions.html#conditions-kms-encryption-context) – Use this condition key with the `kms:GenerateDataKey`, `kms:Decrypt`, and `kms:CreateGrant` actions\.

In the following example, the policy authorizes AWS account `444455556666` to use version 1 of the specified classifier model owned by AWS account `111122223333`\.

**Example KMS key policy to access a specific classifier model version**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
          "AWS":
                "arn:aws:iam::444455556666:root"
      },
      "Action": [
          "kms:Decrypt",
          "kms:GenerateDataKey"
      ],
      "Resource": "*",
      "Condition": {
          "StringEquals": {
              "aws:SourceArn":
                "arn:aws:comprehend:us-west-2:111122223333:document-classifier/classifierName/version/1"
          }
      }
    },
    {
      "Effect": "Allow",
      "Principal": {
          "AWS":  "arn:aws:iam::444455556666:root"
      },
      "Action": "kms:CreateGrant",
      "Resource": "*",
      "Condition": {
        "StringEquals": {
           "kms:EncryptionContext:aws:comprehend:arn":
              "arn:aws:comprehend:us-west-2:111122223333:document-classifier/classifierName/version/1"
        }
      }
    }
  ]
}
```

The following example policy authorizes user **ExampleUser **from AWS account `444455556666` and **ExampleRole** from AWS account `123456789012` to access this KMS key via the Amazon Comprehend service\. 

**Example KMS key policy to allow access to the Amazon Comprehend service \(alternative 1\)\.**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
        "Effect": "Allow",
        "Principal": {
            "AWS": [
                "arn:aws:iam::444455556666:user/ExampleUser",
                "arn:aws:iam::123456789012:role/ExampleRole"
              ]
        },
        "Action": [
            "kms:Decrypt",
            "kms:GenerateDataKey"
        ],
        "Resource": "*",
        "Condition": {
            "StringLike": {
                "aws:SourceArn": "arn:aws:comprehend:*"

            }
        }
    },
    {
      "Effect": "Allow",
      "Principal": {
         "AWS": [
                "arn:aws:iam::444455556666:user/ExampleUser",
                "arn:aws:iam::123456789012:role/ExampleRole"
              ]
      },
      "Action": "kms:CreateGrant",
      "Resource": "*",
      "Condition": {
          "StringLike": {
              "kms:EncryptionContext:aws:comprehend:arn": "arn:aws:comprehend:*"
          }
      }
    }
  ]
}
```

The following example policy authorizes AWS account `444455556666` to access this KMS key via the Amazon Comprehend service, using an alternative syntax to the previous example\. 

**Example KMS key policy to allow access to the Amazon Comprehend service \(alternative 2\)\.**  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
          "AWS": "arn:aws:iam::444455556666:root"
      },
      "Action": [
          "kms:Decrypt",
          "kms:GenerateDataKey",
          "kms:CreateGrant"
      ],
      "Resource": "*",
      "Condition": {
          "StringLike": {
              "kms:EncryptionContext:aws:comprehend:arn": "arn:aws:comprehend:*"
          }
      }
    }
  ]
}
```

For more information, see [Key policies in AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/key-policies.html) in the *AWS Key Management Service Developer Guide*\.

## Resource\-based policies for custom models<a name="custom-copy-sharing-example-policy"></a>

Before an Amazon Comprehend user in another AWS account can import a custom model from your AWS account, you must authorize them to do so\. To authorize them, you add a *resource\-based policy* to the model version that you want to share\. A resource\-based policy is an IAM policy that you attach to a resource in AWS\. 

When you attach a resource policy to a custom model version, the policy authorizes users, groups, or roles to perform the `comprehend:ImportModel` action on the model version\.

**Example Resource\-based policy for a custom model version**  
This example specifies the authorized entities in the `Principal` attribute\. Resource "\*" refers to the specific model version that you attach the policy to\.  

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "comprehend:ImportModel",
      "Resource": "*",
      "Principal": {
        "AWS": [
                "arn:aws:iam::111122223333:root",
                "arn:aws:iam::444455556666:user/ExampleUser",
                "arn:aws:iam::123456789012:role/ExampleRole"
         ]
      }
    }
  ]
}
```
For policies that you attach to custom models, `comprehend:ImportModel` is the only action that Amazon Comprehend supports\.  
For more information about resource\-based policies, see [Identity\-based policies and resource\-based policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_identity-vs-resource.html) in the *IAM User Guide*\.

## Step 1: Add a resource\-based policy to a custom model<a name="custom-copy-sharing-adding-policy"></a>

You can add a resource\-based policy by using the AWS Management Console, AWS CLI, or Amazon Comprehend API\.

### AWS Management Console<a name="custom-copy-sharing-adding-policy-console"></a>

You can use Amazon Comprehend in the AWS Management Console\.

**To add a resource\-based policy**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. In the navigation menu on the left, under **Customization**, choose the page that contains your custom model: 

   1. If you are sharing a custom document classifier, choose **Custom classification**\.

   1. If you are sharing a custom entity recognizer, choose **Custom entity recognition**\.

1. In the list of models, choose the model name to open its details page\.

1. Under **Versions**, choose the name of the model version that you want to share\.

1. On the version details page, choose the **Tags, VPC & Policy** tab\.

1. In the **Resource\-based policy** section, choose **Edit**\.

1. On the **Edit resource\-based policy page**, do the following:

   1. For **Policy name**, enter a name that will help you recognize the policy after you create it\.

   1. Under **Authorize**, specify one or more of the following entities to authorize them to import your model:    
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/comprehend/latest/dg/custom-copy-sharing.html)

1. Under **Share**, you can copy the ARN of the model version to help you share it with the person who will import your model\. When someone imports a custom model from a different AWS account, the model version ARN is required\.

1. Choose **Save**\. Amazon Comprehend creates your resource\-based policy and attaches it to your model\.

### AWS CLI<a name="custom-copy-sharing-adding-policy-cli"></a>

To add a resource\-based policy to a custom model with the AWS CLI, use the [PutResourcePolicy](https://docs.aws.amazon.com/comprehend/latest/dg/API_PutResourcePolicy.html) command\. The command takes the following parameters:
+ `resource-arn` – The ARN of the custom model, including the model version\. 
+ `resource-policy` – A JSON file that defines the resource\-based policy to attach to your custom model\. 

  You can also provide the policy as an inline JSON string\. To provide valid JSON for your policy, enclose the attribute names and values in double quotes\. If the JSON body is also enclosed in double quotes, you escape the double quotes that are inside the policy\.
+ `policy-revision-id` – The revision ID that Amazon Comprehend assigned to the policy that you are updating\. If you are creating a new policy that has no prior version, don't use this parameter\. Amazon Comprehend creates the revision ID for you\.

**Example Add a resource\-based policy to a custom model using the `put-resource-policy` command**  
This example defines a policy in a JSON file named **policyFile\.json** and associates the policy to a model\. The model is version **v2** of a classifier named **mycf1**\.   

```
$ aws comprehend put-resource-policy \
> --resource-arn arn:aws:comprehend:us-west-2:111122223333:document-classifier/mycf1/version/v2 \
> --resource-policy file://policyFile.json \
> --policy-revision-id revision-id
```
The JSON file for the resource policy contains the following contents:  
+ *Action* – The policy authorizes the named principals to use `comprehend:ImportModel`\. 
+ *Resource* – The ARN of the custom model\. Resource "\*" refers to the model version that you specify in the `put-resource-policy` command\.
+ *Principal* – The policy authorizes user `jane` from AWS account 444455556666 and all users from AWS account 123456789012\.

```
{
"Version":"2012-10-17",
 "Statement":[
    {"Sid":"ResourcePolicyForImportModel",
     "Effect":"Allow",
     "Action":["comprehend:ImportModel"],
     "Resource":"*",
     "Principal":
         {"AWS":
            ["arn:aws:iam::444455556666:user/jane",
             "123456789012"]
         }
   }
 ]
}
```

### Amazon Comprehend API<a name="custom-copy-sharing-adding-policy-api"></a>

To add a resource\-based policy to a custom model by using the Amazon Comprehend API, use the [PutResourcePolicy](https://docs.aws.amazon.com/comprehend/latest/dg/API_PutResourcePolicy.html) API operation\. 

You can also add a policy to a custom model in the API request that creates the model\. To do this, provide the policy JSON for the ModelPolicy parameter when you submit a [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateDocumentClassifier.html) or [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateEntityRecognizer.html) request\. 

## Step 2: Provide the details that others need to import<a name="custom-copy-sharing-details"></a>

Now that you have added the resource\-based policy to your custom model, you have authorized other Amazon Comprehend users to import your model into their AWS accounts\. However, before they can import, you must provide them with the following details:
+ The Amazon Resource Name \(ARN\) of the model version\.
+ The AWS Region that contains the model\. Anyone who imports your model must use the same AWS Region \.
+ Whether the model is encrypted, and if it is, the type of AWS KMS key that you use: AWS owned key or customer managed key\.
+ If your model is encrypted with a customer managed key, then you must provide the ARN of the KMS key\. Anyone who imports your model must include the ARN in an IAM service role in their AWS account\. This role authorizes Amazon Comprehend to use the KMS key to decrypt the model during the import\.

For more information about how other users import your model, see [Importing a custom model from another AWS account](custom-copy-importing.md)\.