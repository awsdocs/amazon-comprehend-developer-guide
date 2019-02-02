# DocumentClassificationJobProperties<a name="API_DocumentClassificationJobProperties"></a>

Provides information about a document classification job\.

## Contents<a name="API_DocumentClassificationJobProperties_Contents"></a>

 **DataAccessRoleArn**   <a name="comprehend-Type-DocumentClassificationJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **DocumentClassifierArn**   <a name="comprehend-Type-DocumentClassificationJobProperties-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\.   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 **EndTime**   <a name="comprehend-Type-DocumentClassificationJobProperties-EndTime"></a>
The time that the document classification job completed\.  
Type: Timestamp  
Required: No

 **InputDataConfig**   <a name="comprehend-Type-DocumentClassificationJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the document classification job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 **JobId**   <a name="comprehend-Type-DocumentClassificationJobProperties-JobId"></a>
The identifier assigned to the document classification job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobName**   <a name="comprehend-Type-DocumentClassificationJobProperties-JobName"></a>
The name that you assigned to the document classification job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-DocumentClassificationJobProperties-JobStatus"></a>
The current status of the document classification job\. If the status is `FAILED`, the `Message` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **Message**   <a name="comprehend-Type-DocumentClassificationJobProperties-Message"></a>
A description of the status of the job\.  
Type: String  
Required: No

 **OutputDataConfig**   <a name="comprehend-Type-DocumentClassificationJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the document classification job\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 **SubmitTime**   <a name="comprehend-Type-DocumentClassificationJobProperties-SubmitTime"></a>
The time that the document classification job was submitted for processing\.  
Type: Timestamp  
Required: No

## See Also<a name="API_DocumentClassificationJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassificationJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassificationJobProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DocumentClassificationJobProperties) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DocumentClassificationJobProperties) 