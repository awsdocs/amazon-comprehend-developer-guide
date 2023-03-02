# Importing a custom model from another AWS account<a name="custom-copy-importing"></a>

In Amazon Comprehend, you can import a custom model that's in another AWS account\. When you import a model, you create a new custom model in your account\. Your new custom model is a fully\-trained duplicate of the model that you imported\.

**Topics**
+ [Before you begin](#custom-copy-importing-prerequisites)
+ [Importing a custom model](#custom-copy-importing-procedure)

## Before you begin<a name="custom-copy-importing-prerequisites"></a>

Before you can import a custom model from another AWS account, ensure that the person who shared the model with you does the following:
+ Authorizes you to do the import\. This authorization is granted in the resource\-based policy that is attached to the model version\. For more information, see [Resource\-based policies for custom models](custom-copy-sharing.md#custom-copy-sharing-example-policy)\.
+ Provides you with the following information:
  + The Amazon Resource Name \(ARN\) of the model version\.
  + The AWS Region that contains the model\. You must use the same AWS Region when you import\.
  + Whether the model is encrypted with an AWS KMS key and, if it is, the type of key that is used\. 

If the model is encrypted, you might need to take additional steps, depending on the type of KMS key that is used:
+ **AWS owned key** – This type of KMS key is owned and managed by AWS\. If the model is encrypted with an AWS owned key, no additional steps are needed\.
+ **Customer managed key** – This type of KMS key is created, owned, and managed by an AWS customer in their AWS account\. If the model is encrypted with a customer managed key, then the person who shared the model must:
  + Authorize you to decrypt the model\. This authorization is granted in the KMS key policy for the customer managed key\. For more information, see [AWS KMS key policy statement](custom-copy-sharing.md#custom-copy-sharing-prerequisites-permissions-kms)\.
  + Provide the ARN of the customer managed key\. You use this ARN when you create an IAM service role\. This role authorizes Amazon Comprehend to use the KMS key to decrypt the model\.

### Required permissions<a name="custom-copy-importing-prerequisites-permissions"></a>

Before you can import a custom model, you or your administrator must authorize the required actions in AWS Identity and Access Management \(IAM\)\. As an Amazon Comprehend user, you must be authorized to import by an IAM policy statement\. If encryption or decryption is required during the import, then Amazon Comprehend must be authorized to use the necessary AWS KMS keys\.

### IAM policy statement<a name="custom-copy-importing-prerequisites-permissions-iam"></a>

Your user, group or role must have a policy attached that allows the `ImportModel` action, as shown in the following example\.

**Example IAM policy to import a custom model**  

```
{ 
  "Effect": "Allow",
  "Action": [
    "comprehend:ImportModel"
  ],
  "Resource": "arn:aws:comprehend:us-west-2:111122223333:document-classifier/foo/version/*"
}
```

For information about creating an IAM policy, see [Creating IAM policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html) in the *IAM User Guide*\. For information about attaching an IAM policy, see [Adding and removing IAM identity permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_manage-attach-detach.html) in the *IAM User Guide*\.

### IAM service role for AWS KMS encryption<a name="custom-copy-importing-prerequisites-permissions-kms"></a>

When you import a custom model, you must authorize Amazon Comprehend to use AWS KMS keys in either of the following cases:
+ You are importing a custom model that is encrypted with a customer managed key in AWS KMS\. In this case, Amazon Comprehend needs access to the KMS key so that it can decrypt the model during the import\.
+ You want to encrypt the new custom model that you create with the import, and you want to use a customer managed key\. In this case, Amazon Comprehend needs access to your KMS key so that it can encrypt the new model\.

To authorize Amazon Comprehend to use these AWS KMS keys, you create an *IAM service role*\. This type of IAM role allows an AWS service to access resources in other services on your behalf\. For more information about service roles, see [Creating a role to delegate permissions to an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\.

If you use the Amazon Comprehend console to import, you can have Amazon Comprehend create the service role for you\. Otherwise, you must create a service role in IAM before you import\.

The IAM service role must have a permissions policy and a trust policy, as shown by the following examples\.

**Example permissions policy**  
The following permissions policy allows the AWS KMS operations that Amazon Comprehend uses to encrypt and decrypt custom models\. It grants access to two KMS keys:  
+ One KMS key is in the AWS account that contains the model to import\. It was used to encrypt the model, and Amazon Comprehend uses it to decrypt the model during the import\.
+ The other KMS key is in the AWS account that imports the model\. Amazon Comprehend uses this key to encrypt the new custom model that is created by the import\.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
        "Effect": "Allow",
        "Action": [
            "kms:CreateGrant"
        ],
        "Resource": [
            "arn:aws:kms:us-west-2:111122223333:key/key-id",
            "arn:aws:kms:us-west-2:444455556666:key/key-id"
        ]
    },
    {
        "Effect": "Allow",
        "Action": [
            "kms:Decrypt",
            "kms:GenerateDatakey"
        ],
        "Resource": [
            "arn:aws:kms:us-west-2:111122223333:key/key-id",
            "arn:aws:kms:us-west-2:444455556666:key/key-id"
        ],
        "Condition": {
            "StringEquals": {
                "kms:ViaService": [
                    "s3.us-west-2.amazonaws.com"
                ]
            }
        }
    }
  ]
}
```

**Example trust policy**  

The following trust policy allows Amazon Comprehend to assume the role and gain its permissions\. It allows the `comprehend.amazonaws.com` service principal to perform the `sts:AssumeRole` operation\. To help with [confused deputy prevention](cross-service-confused-deputy-prevention.md), you restrict the scope of the permission by using one or more global condition context keys\. For `aws:SourceAccount`, specify the account Id of the user who is importing the model\. 

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "comprehend.amazonaws.com"
      },
      "Action": "sts:AssumeRole",
      "Condition": {
        "StringEquals": {
          "aws:SourceAccount": "444455556666"  
        }
      }
    }
  ]
}
```

## Importing a custom model<a name="custom-copy-importing-procedure"></a>

You can import a custom model by using the AWS Management Console, AWS CLI, or Amazon Comprehend API\.

## AWS Management Console<a name="custom-copy-importing-procedure-console"></a>

You can use Amazon Comprehend in the AWS Management Console\.

**To import a custom model**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. In the navigation menu on the left, under **Customization**, choose the page for the type of model that you are importing:

   1. If you are importing a custom document classifier, choose **Custom classification**\.

   1. If you are importing a custom entity recognizer, choose **Custom entity recognition**\.

1. Choose **Import version**\.

1. On the **Import model version** page, enter the following details:
   + **Model version ARN** – The ARN of the model version to import\.
   + **Model name** – A custom name for the new model that is created by the import\.
   + **Version name** – A custom name for the new model version that is created by the import\.

1. For **Model encryption**, choose the type of KMS key to use to encrypt the new custom model that you create with the import:
   + **Use AWS owned key** – Amazon Comprehend encrypts your model by using a key in AWS Key Management Service \(AWS KMS\) that is created, managed, and used on your behalf by AWS\.
   + **Choose a different AWS KMS key \(advanced\)** – Amazon Comprehend encrypts your model by using a customer managed key that you manage in AWS KMS\.

     If you choose this option, select a KMS key that's in your AWS account, or create a new one by choosing **Create an AWS KMS key**\.

1. In the **Service access** section, grant Amazon Comprehend access to any AWS KMS keys that it needs to:
   + Decrypt the custom model that you import\.
   + Encrypt that the new custom model that you create with the import\.

   You grant access with an IAM service role that allows Amazon Comprehend to use the KMS keys\.

   For **Service role**, do one of the following:
   + If you have an existing service role that you want to use, choose **Use an existing IAM role**\. Then, select it under **Role name**\.
   + If you want Amazon Comprehend to create a role for you, choose **Create an IAM role**\.

1. If you chose to have Amazon Comprehend create the role for you, do the following:

   1. For **Role name**, enter a role name suffix that will help you recognize the role later\.

   1. For **Source KMS key ARN**, enter the ARN of the KMS key that is used to encrypt the model that you're importing\. Amazon Comprehend uses this key to decrypt the model during the import\.

1. \(Optional\) In the **Tags** section, you can add tags to the new custom model that you create by importing\. For more information about tagging custom models, see [Tagging a new resource](tagging-newtags.md)\.

1. Choose **Confirm**\.

## AWS CLI<a name="custom-copy-importing-procedure-cli"></a>

You can use Amazon Comprehend by running commands with the AWS CLI\.

**Example Import\-model command**  
To import a custom model, use the `import-model` command:  

```
$ aws comprehend import-model \
> --source-model arn:aws:comprehend:us-west-2:111122223333:document-classifier/foo/version/bar \
> --model-name importedDocumentClassifier \
> --version-name versionOne \
> --data-access-role-arn arn:aws:iam::444455556666:role/comprehendAccessRole \
> --model-kms-key-id kms-key-id
```
This example uses the following parameters:  
+ `source-model` – The ARN of the custom model to import\.
+ `model-name` – A custom name for the new model that is created by the import\.
+ `version-name` – A custom name for the new model version that is created by the import\.
+ `data-access-role-arn` – The ARN of the IAM service role that allows Amazon Comprehend to use the necessary AWS KMS keys to encrypt or decrypt the custom model\.
+ `model-kms-key-id` – The ARN or ID of the KMS key that Amazon Comprehend uses to encrypt the custom model that you create with this import\. This key must be in AWS KMS in your AWS account\.

## Amazon Comprehend API<a name="custom-copy-importing-procedure-api"></a>

To import a custom model by using the Amazon Comprehend API, use the [ImportModel](https://docs.aws.amazon.com/comprehend/latest/dg/API_ImportModel.html) API action\. 