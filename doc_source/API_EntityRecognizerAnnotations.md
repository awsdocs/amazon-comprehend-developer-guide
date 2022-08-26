# EntityRecognizerAnnotations<a name="API_EntityRecognizerAnnotations"></a>

Describes the annotations associated with a entity recognizer\.

## Contents<a name="API_EntityRecognizerAnnotations_Contents"></a>

 ** S3Uri **   <a name="comprehend-Type-EntityRecognizerAnnotations-S3Uri"></a>
 Specifies the Amazon S3 location where the annotations for an entity recognizer are located\. The URI must be in the same region as the API endpoint that you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

 ** TestS3Uri **   <a name="comprehend-Type-EntityRecognizerAnnotations-TestS3Uri"></a>
 Specifies the Amazon S3 location where the test annotations for an entity recognizer are located\. The URI must be in the same region as the API endpoint that you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: No

## See Also<a name="API_EntityRecognizerAnnotations_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerAnnotations) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerAnnotations) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerAnnotations) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerAnnotations) 