# KMS Encryption in Amazon Comprehend<a name="kms-in-comprehend"></a>

Amazon Comprehend works with AWS Key Management Service \(AWS KMS\) to provide enhanced encryption for your data\. Amazon S3 already enables you to encrypt your input documents when creating a text analysis, topic modeling, or custom Amazon Comprehend job\. Integration with AWS KMS enables you to encrypt the data in the storage volume for Start\* and Create\* jobs, and it encrypts the output results of Start\* jobs using your own KMS key\.

For the AWS Management Console, Amazon Comprehend encrypts custom models with its own KMS key\. For the AWS CLI, Amazon Comprehend can encrypt custom models using either its own KMS key or a provided customer managed key \(CMK\)\.

**KMS encryption using the AWS Management Console** 

Two encryption options are available when using the console:
+ Volume encryption
+ Output result encryption

**To enable volume encryption**

1.  Under **Job Settings**, choose the **Job encryption** option\.   
![\[KMS Job encryption in the AWS Management Console\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/kms-1.png)

1. Choose whether the KMS customer\-managed key \(CMK\) is from the account you're currently using or from a different account\. If you want to use a key from the current account, choose the key alias from **KMS key ID**\. If you're using a key from a different account, you must enter the key's ARN\.

**To enable output result encryption**

1.  Under **Output Settings**, choose the **Encryption** option\.   
![\[KMS output result encryption in the AWS Management Console\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/kms-2.png)

1. Choose whether the customer\-managed key \(CMK\) is from the account you're currently using or from a different account\. If you want to use a key from the current account, choose the key ID from **KMS key ID**\. If you're using a key from a different account, you must enter the key's ARN\.

If you have previously setup encryption using SSE\-KMS on the your S3 input documents, this can provide you with additional security\. However, if you do this, the IAM role used must have `kms:Decrypt` permission for the KMS key with which the input documents are encrypted\. For more information, see [Permissions Required to Use KMS Encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

**KMS encryption with API operations** 

All Amazon Comprehend `Start*` and `Create*` API operations support KMS encrypted input documents\. `Describe*` and `List*` API operations return the `KmsKeyId` in `OutputDataConfig` if the original job had `KmsKeyId` provided as an input\. If it was not provided as input, it isn't returned\. 

This can be seen in the following AWS CLI example using the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation:

 

```
aws comprehend start-entities-detection-job \
     --region region \
     --data-access-role-arn "data access role arn" \    
     --entity-recognizer-arn "entity recognizer arn" \
     --input-data-config "S3Uri=s3://Bucket Name/Bucket Path" \    
     --job-name job name \
     --language-code en \
     --output-data-config "KmsKeyId=Output S3 KMS key ID" "S3Uri=s3://Bucket Name/Bucket Path/" \
     --volumekmskeyid "Volume KMS key ID"
```

**Note**  
This example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

**Customer Managed Key \(CMK\) encryption with API operations** 

Amazon Comprehend custom model API operations, `CreateEntityRecognizer`, `CreateDocumentClassifier`, and `CreateEndpoint`, support encryption using customer managed keys via the AWS CLI\.

You need an IAM policy to allow a principal to use or manage customer managed keys\. These keys are specified in the `Resource` element of the policy statement\. As best practice, limit customer managed keys to only those that the principals must use in your policy statement\.

The following AWS CLI example creates a custom entity recognizer with model encryption using the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation:



```
aws comprehend create-entity-recognizer \
     --recognizer-name name \
     --data-access-role-arn data access role arn \    
     --language-code en \
     --model-kms-key-id Model KMS Key ID \ 
     --input-data-config file:///path/input-data-config.json
```

**Note**  
This example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.