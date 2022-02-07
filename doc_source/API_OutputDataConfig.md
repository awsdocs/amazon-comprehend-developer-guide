# OutputDataConfig<a name="API_OutputDataConfig"></a>

Provides configuration parameters for the output of topic detection jobs\.



## Contents<a name="API_OutputDataConfig_Contents"></a>

 ** KmsKeyId **   <a name="comprehend-Type-OutputDataConfig-KmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt the output results from an analysis job\. The KmsKeyId can be one of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ KMS Key Alias: `"alias/ExampleAlias"` 
+ ARN of a KMS Key Alias: `"arn:aws:kms:us-west-2:111122223333:alias/ExampleAlias"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `^\p{ASCII}+$`   
Required: No

 ** S3Uri **   <a name="comprehend-Type-OutputDataConfig-S3Uri"></a>
When you use the `OutputDataConfig` object with asynchronous operations, you specify the Amazon S3 location where you want to write the output data\. The URI must be in the same region as the API endpoint that you are calling\. The location is used as the prefix for the actual location of the output file\.  
When the topic detection job is finished, the service creates an output file in a directory specific to the job\. The `S3Uri` field contains the location of the output file, called `output.tar.gz`\. It is a compressed archive that contains the ouput of the operation\.  
 For a PII entity detection job, the output file is plain text, not a compressed archive\. The output file name is the same as the input file, with `.out` appended at the end\.   
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_OutputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/OutputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/OutputDataConfig) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/OutputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/OutputDataConfig) 