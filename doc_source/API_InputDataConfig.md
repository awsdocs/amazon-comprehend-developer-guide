# InputDataConfig<a name="API_InputDataConfig"></a>

The input properties for a topic detection job\.

## Contents<a name="API_InputDataConfig_Contents"></a>

 **InputFormat**   <a name="comprehend-Type-InputDataConfig-InputFormat"></a>
Specifies how the text in an input file should be processed:  

+  `ONE_DOC_PER_FILE` \- Each file is considered a separate document\. Use this option when you are processing large documents, such as newspaper articles or scientific papers\.

+  `ONE_DOC_PER_LINE` \- Each line in a file is considered a separate document\. Use this option when you are processing many short documents, such as text messages\.
Type: String  
Valid Values:` ONE_DOC_PER_FILE | ONE_DOC_PER_LINE`   
Required: No

 **S3Uri**   <a name="comprehend-Type-InputDataConfig-S3Uri"></a>
The Amazon S3 URI for the input data\. The URI must be in same region as the API endpoint that you are calling\. The URI can point to a single input file or it can provide the prefix for a collection of data files\.   
For example, if you use the URI `S3://bucketName/prefix`, if the prefix is a single file, Amazon Comprehend uses that file as input\. If more than one file begins with the prefix, Amazon Comprehend uses all of them as input\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://([^/]+)(/.*)?`   
Required: Yes

## See Also<a name="API_InputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/InputDataConfig) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/InputDataConfig) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/InputDataConfig) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/InputDataConfig) 