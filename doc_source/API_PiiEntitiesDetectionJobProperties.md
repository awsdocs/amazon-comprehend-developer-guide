# PiiEntitiesDetectionJobProperties<a name="API_PiiEntitiesDetectionJobProperties"></a>

Provides information about a PII entities detection job\.

## Contents<a name="API_PiiEntitiesDetectionJobProperties_Contents"></a>

 ** DataAccessRoleArn **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) that gives Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** EndTime **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-EndTime"></a>
The time that the PII entities detection job completed\.  
Type: Timestamp  
Required: No

 ** InputDataConfig **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-InputDataConfig"></a>
The input properties for a PII entities detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 ** JobArn **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-JobArn"></a>
The Amazon Resource Name \(ARN\) of the PII entities detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:pii-entities-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:pii-entities-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** JobId **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-JobId"></a>
The identifier assigned to the PII entities detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobName **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-JobName"></a>
The name that you assigned the PII entities detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobStatus **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-JobStatus"></a>
The current status of the PII entities detection job\. If the status is `FAILED`, the `Message` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 ** LanguageCode **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-LanguageCode"></a>
The language code of the input documents  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 ** Message **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-Message"></a>
A description of the status of a job\.  
Type: String  
Required: No

 ** Mode **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-Mode"></a>
Specifies whether the output provides the locations \(offsets\) of PII entities or a file in which PII entities are redacted\.  
Type: String  
Valid Values:` ONLY_REDACTION | ONLY_OFFSETS`   
Required: No

 ** OutputDataConfig **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the PII entities detection job\.  
Type: [PiiOutputDataConfig](API_PiiOutputDataConfig.md) object  
Required: No

 ** RedactionConfig **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-RedactionConfig"></a>
Provides configuration parameters for PII entity redaction\.  
This parameter is required if you set the `Mode` parameter to `ONLY_REDACTION`\. In that case, you must provide a `RedactionConfig` definition that includes the `PiiEntityTypes` parameter\.  
Type: [RedactionConfig](API_RedactionConfig.md) object  
Required: No

 ** SubmitTime **   <a name="comprehend-Type-PiiEntitiesDetectionJobProperties-SubmitTime"></a>
The time that the PII entities detection job was submitted for processing\.  
Type: Timestamp  
Required: No

## See Also<a name="API_PiiEntitiesDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/PiiEntitiesDetectionJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/PiiEntitiesDetectionJobProperties) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/PiiEntitiesDetectionJobProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/PiiEntitiesDetectionJobProperties) 