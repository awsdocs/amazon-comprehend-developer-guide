# EntityRecognizerDocuments<a name="API_EntityRecognizerDocuments"></a>

Describes the training documents submitted with an entity recognizer\.

## Contents<a name="API_EntityRecognizerDocuments_Contents"></a>

 ** InputFormat **   <a name="comprehend-Type-EntityRecognizerDocuments-InputFormat"></a>
 Specifies how the text in an input file should be processed\. This is optional, and the default is ONE\_DOC\_PER\_LINE\. ONE\_DOC\_PER\_FILE \- Each file is considered a separate document\. Use this option when you are processing large documents, such as newspaper articles or scientific papers\. ONE\_DOC\_PER\_LINE \- Each line in a file is considered a separate document\. Use this option when you are processing many short documents, such as text messages\.  
Type: String  
Valid Values:` ONE_DOC_PER_FILE | ONE_DOC_PER_LINE`   
Required: No

 ** S3Uri **   <a name="comprehend-Type-EntityRecognizerDocuments-S3Uri"></a>
 Specifies the Amazon S3 location where the training documents for an entity recognizer are located\. The URI must be in the same region as the API endpoint that you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

 ** TestS3Uri **   <a name="comprehend-Type-EntityRecognizerDocuments-TestS3Uri"></a>
 Specifies the Amazon S3 location where the test documents for an entity recognizer are located\. The URI must be in the same AWS Region as the API endpoint that you are calling\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: No

## See Also<a name="API_EntityRecognizerDocuments_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerDocuments) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerDocuments) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerDocuments) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerDocuments) 