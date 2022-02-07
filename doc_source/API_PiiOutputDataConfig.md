# PiiOutputDataConfig<a name="API_PiiOutputDataConfig"></a>

Provides configuration parameters for the output of PII entity detection jobs\.

## Contents<a name="API_PiiOutputDataConfig_Contents"></a>

 ** KmsKeyId **   <a name="comprehend-Type-PiiOutputDataConfig-KmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt the output results from an analysis job\.  
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `^\p{ASCII}+$`   
Required: No

 ** S3Uri **   <a name="comprehend-Type-PiiOutputDataConfig-S3Uri"></a>
When you use the `PiiOutputDataConfig` object with asynchronous operations, you specify the Amazon S3 location where you want to write the output data\.   
 For a PII entity detection job, the output file is plain text, not a compressed archive\. The output file name is the same as the input file, with `.out` appended at the end\.   
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_PiiOutputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/PiiOutputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/PiiOutputDataConfig) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/PiiOutputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/PiiOutputDataConfig) 