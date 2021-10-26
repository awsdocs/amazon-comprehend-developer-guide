# DocumentClassifierInputDataConfig<a name="API_DocumentClassifierInputDataConfig"></a>

The input properties for training a document classifier\. 

For more information on how the input file is formatted, see [Creating Training Data](how-document-classification-training.md#how-document-classification-training-data)\. 

## Contents<a name="API_DocumentClassifierInputDataConfig_Contents"></a>

 **LabelDelimiter**   <a name="comprehend-Type-DocumentClassifierInputDataConfig-LabelDelimiter"></a>
Indicates the delimiter used to separate each label for training a multi\-label classifier\. The default delimiter between labels is a pipe \(\|\)\. You can use a different character as a delimiter \(if it's an allowed character\) by specifying it under Delimiter for labels\. If the training documents use a delimiter other than the default or the delimiter you specify, the labels on that line will be combined to make a single unique label, such as LABELLABELLABEL\.  
Type: String  
Length Constraints: Fixed length of 1\.  
Pattern: `^[ ~!@#$%^*\-_+=|\\:;\t>?/]$`   
Required: No

 **S3Uri**   <a name="comprehend-Type-DocumentClassifierInputDataConfig-S3Uri"></a>
The Amazon S3 URI for the input data\. The S3 bucket must be in the same region as the API endpoint that you are calling\. The URI can point to a single input file or it can provide the prefix for a collection of input files\.  
For example, if you use the URI `S3://bucketName/prefix`, if the prefix is a single file, Amazon Comprehend uses that file as input\. If more than one file begins with the prefix, Amazon Comprehend uses all of them as input\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

## See Also<a name="API_DocumentClassifierInputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassifierInputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassifierInputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DocumentClassifierInputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DocumentClassifierInputDataConfig) 