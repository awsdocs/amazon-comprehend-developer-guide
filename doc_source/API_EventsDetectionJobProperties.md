# EventsDetectionJobProperties<a name="API_EventsDetectionJobProperties"></a>

Provides information about an events detection job\.

## Contents<a name="API_EventsDetectionJobProperties_Contents"></a>

 ** DataAccessRoleArn **   <a name="comprehend-Type-EventsDetectionJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identify and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** EndTime **   <a name="comprehend-Type-EventsDetectionJobProperties-EndTime"></a>
The time that the events detection job completed\.  
Type: Timestamp  
Required: No

 ** InputDataConfig **   <a name="comprehend-Type-EventsDetectionJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the events detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 ** JobArn **   <a name="comprehend-Type-EventsDetectionJobProperties-JobArn"></a>
The Amazon Resource Name \(ARN\) of the events detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:events-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:events-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** JobId **   <a name="comprehend-Type-EventsDetectionJobProperties-JobId"></a>
The identifier assigned to the events detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobName **   <a name="comprehend-Type-EventsDetectionJobProperties-JobName"></a>
The name you assigned the events detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobStatus **   <a name="comprehend-Type-EventsDetectionJobProperties-JobStatus"></a>
The current status of the events detection job\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 ** LanguageCode **   <a name="comprehend-Type-EventsDetectionJobProperties-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 ** Message **   <a name="comprehend-Type-EventsDetectionJobProperties-Message"></a>
A description of the status of the events detection job\.  
Type: String  
Required: No

 ** OutputDataConfig **   <a name="comprehend-Type-EventsDetectionJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the events detection job\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 ** SubmitTime **   <a name="comprehend-Type-EventsDetectionJobProperties-SubmitTime"></a>
The time that the events detection job was submitted for processing\.  
Type: Timestamp  
Required: No

 ** TargetEventTypes **   <a name="comprehend-Type-EventsDetectionJobProperties-TargetEventTypes"></a>
The types of events that are detected by the job\.  
Type: Array of strings  
Array Members: Minimum number of 1 item\.  
Length Constraints: Minimum length of 1\. Maximum length of 40\.  
Pattern: `[A-Z_]*`   
Required: No

## See Also<a name="API_EventsDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EventsDetectionJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EventsDetectionJobProperties) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EventsDetectionJobProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EventsDetectionJobProperties) 