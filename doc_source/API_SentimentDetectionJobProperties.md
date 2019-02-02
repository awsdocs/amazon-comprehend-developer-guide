# SentimentDetectionJobProperties<a name="API_SentimentDetectionJobProperties"></a>

Provides information about a sentiment detection job\.

## Contents<a name="API_SentimentDetectionJobProperties_Contents"></a>

 **DataAccessRoleArn**   <a name="comprehend-Type-SentimentDetectionJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) that gives Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **EndTime**   <a name="comprehend-Type-SentimentDetectionJobProperties-EndTime"></a>
The time that the sentiment detection job ended\.  
Type: Timestamp  
Required: No

 **InputDataConfig**   <a name="comprehend-Type-SentimentDetectionJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the sentiment detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 **JobId**   <a name="comprehend-Type-SentimentDetectionJobProperties-JobId"></a>
The identifier assigned to the sentiment detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobName**   <a name="comprehend-Type-SentimentDetectionJobProperties-JobName"></a>
The name that you assigned to the sentiment detection job  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-SentimentDetectionJobProperties-JobStatus"></a>
The current status of the sentiment detection job\. If the status is `FAILED`, the `Messages` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **LanguageCode**   <a name="comprehend-Type-SentimentDetectionJobProperties-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: No

 **Message**   <a name="comprehend-Type-SentimentDetectionJobProperties-Message"></a>
A description of the status of a job\.  
Type: String  
Required: No

 **OutputDataConfig**   <a name="comprehend-Type-SentimentDetectionJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the sentiment detection job\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 **SubmitTime**   <a name="comprehend-Type-SentimentDetectionJobProperties-SubmitTime"></a>
The time that the sentiment detection job was submitted for processing\.  
Type: Timestamp  
Required: No

## See Also<a name="API_SentimentDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/SentimentDetectionJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/SentimentDetectionJobProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/SentimentDetectionJobProperties) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/SentimentDetectionJobProperties) 