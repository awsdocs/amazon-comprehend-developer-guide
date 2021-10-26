# DocumentClassifierOutputDataConfig<a name="API_DocumentClassifierOutputDataConfig"></a>

Provides output results configuration parameters for custom classifier jobs\. 

## Contents<a name="API_DocumentClassifierOutputDataConfig_Contents"></a>

 **KmsKeyId**   <a name="comprehend-Type-DocumentClassifierOutputDataConfig-KmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt the output results from an analysis job\. The KmsKeyId can be one of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ KMS Key Alias: `"alias/ExampleAlias"` 
+ ARN of a KMS Key Alias: `"arn:aws:kms:us-west-2:111122223333:alias/ExampleAlias"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Required: No

 **S3Uri**   <a name="comprehend-Type-DocumentClassifierOutputDataConfig-S3Uri"></a>
When you use the `OutputDataConfig` object while creating a custom classifier, you specify the Amazon S3 location where you want to write the confusion matrix\. The URI must be in the same region as the API endpoint that you are calling\. The location is used as the prefix for the actual location of this output file\.  
When the custom classifier job is finished, the service creates the output file in a directory specific to the job\. The `S3Uri` field contains the location of the output file, called `output.tar.gz`\. It is a compressed archive that contains the confusion matrix\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: No

## See Also<a name="API_DocumentClassifierOutputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassifierOutputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassifierOutputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DocumentClassifierOutputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DocumentClassifierOutputDataConfig) 