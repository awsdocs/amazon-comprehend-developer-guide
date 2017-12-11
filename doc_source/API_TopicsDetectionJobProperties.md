# TopicsDetectionJobProperties<a name="API_TopicsDetectionJobProperties"></a>

Provides information about a topic detection job\.

## Contents<a name="API_TopicsDetectionJobProperties_Contents"></a>

 **EndTime**   
The time that the topic detection job was completed\.  
Type: Timestamp  
Required: No

 **InputDataConfig**   
The input data configuration supplied when you created the topic detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 **JobId**   
The identifier assigned to the topic detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Required: No

 **JobName**   
The name of the topic detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   
The current status of the topic detection job\. If the status is `Failed`, the reason for the failure is shown in the `Message` field\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED`   
Required: No

 **Message**   
A description for the status of a job\.  
Type: String  
Required: No

 **NumberOfTopics**   
The number of topics to detect supplied when you created the topic detection job\. The default is 10\.   
Type: Integer  
Required: No

 **OutputDataConfig**   
The output data configuration supplied when you created the topic detection job\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 **SubmitTime**   
The time that the topic detection job was submitted for processing\.  
Type: Timestamp  
Required: No

## See Also<a name="API_TopicsDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/TopicsDetectionJobProperties) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/TopicsDetectionJobProperties) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/TopicsDetectionJobProperties) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/TopicsDetectionJobProperties) 