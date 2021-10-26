# InputDataConfig<a name="API_medical_InputDataConfig"></a>

The input properties for an entities detection job\.

## Contents<a name="API_medical_InputDataConfig_Contents"></a>

 **S3Bucket**   <a name="comprehend-Type-medical_InputDataConfig-S3Bucket"></a>
The URI of the S3 bucket that contains the input data\. The bucket must be in the same region as the API endpoint that you are calling\.  
Each file in the document collection must be less than 40 KB\. You can store a maximum of 30 GB in the bucket\.  
Type: String  
Length Constraints: Minimum length of 3\. Maximum length of 63\.  
Pattern: `^[0-9a-z\.\-_]*(?!\.)$`   
Required: Yes

 **S3Key**   <a name="comprehend-Type-medical_InputDataConfig-S3Key"></a>
The path to the input data files in the S3 bucket\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `.*`   
Required: No

## See Also<a name="API_medical_InputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/InputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/InputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/InputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/InputDataConfig) 