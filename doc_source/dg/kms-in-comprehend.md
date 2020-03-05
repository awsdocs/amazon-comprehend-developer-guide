# KMS Encryption in Amazon Comprehend<a name="kms-in-comprehend"></a>

Amazon Comprehend works with Amazon Key Management Service \(KMS\) to provide enhanced encryption for your data\. Amazon S3 already enables you to encrypt your input documents when creating a text analysis, topic modeling, or custom Comprehend job\. Integration with KMS enables you to encrypt the data in the storage volume for Start\* and Create\* jobs as well as encrypt the output results of Start\* jobs using your own KMS key\. Amazon Comprehend encrypts custom models with its own KMS key and does not use a customer provided KMS key\. 

**KMS encryption with the AWS Console** 

Two encryption options are available when using the AWS Console:
+ Volume encryption
+ Output result encryption

**To enable volume encryption**

1.  Under **Job Settings**, choose the **Job encryption** option\.   
![\[KMS Job encryption in the AWS Console\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/kms-1.png)

1. Choose whether the KMS customer\-managed key \(CMK\) is from the account you're currently using or from a different account\. If you want to use a key from the current account, choose the key alias from **KMS key ID**\. If you're using a key from a different account, you need to enter the key's ARN\.

**To enable output result encryption**

1.  Under **Output Settings**, choose the **Encryption** option\.   
![\[KMS output result encryption in the AWS Console\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/kms-2.png)

1. Choose whether the customer\-managed key \(CMK\) is from the account you're currently using or from a different account\. If you want to use a key from the current account, choose the key ID from **KMS key ID**\. If you're using a key from a different account, you need to enter the key's ARN\.

If you have previously setup encryption using SSE\-KMS on the your S3 input documents, this can provide you with additional security\. However, if you do this, the IAM role used must have `kms:Decrypt` permission for the KMS key with which the input documents are encrypted\. For more information, see [Permissions Required to Use KMS Encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

**KMS encryption with APIs** 

All Amazon Comprehend `Start*` and `Create*` APIs support KMS encrypted input documents\. `Describe*` and `List*` APIs will return the `KmsKeyId` in `OutputDataConfig` if the original job had `KmsKeyId` provided as an input\. If it was not provided as input, it will not be returned\. 

This can be seen in the following AWS CLI example using the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation:

This example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. 

```
aws comprehend start-entities-detection-job \
     --region region
     --data-access-role-arn "data access role arn" \    
     --entity-recognizer-arn "entity recognizer arn" \
     --input-data-config "S3Uri=s3://Bucket Name/Bucket Path" \    
     --job-name job name \
     --language-code en \
     --output-data-config "KmsKeyId=Output S3 KMS key ID" "S3Uri=s3://Bucket Name/Bucket Path/" \
     --volumekmskeyid "Volume KMS key ID"
```