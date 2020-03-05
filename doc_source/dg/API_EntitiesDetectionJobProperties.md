# EntitiesDetectionJobProperties<a name="API_EntitiesDetectionJobProperties"></a>

Provides information about an entities detection job\.

## Contents<a name="API_EntitiesDetectionJobProperties_Contents"></a>

 **DataAccessRoleArn**   <a name="comprehend-Type-EntitiesDetectionJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) that gives Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **EndTime**   <a name="comprehend-Type-EntitiesDetectionJobProperties-EndTime"></a>
The time that the entities detection job completed  
Type: Timestamp  
Required: No

 **EntityRecognizerArn**   <a name="comprehend-Type-EntitiesDetectionJobProperties-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 **InputDataConfig**   <a name="comprehend-Type-EntitiesDetectionJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the entities detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 **JobId**   <a name="comprehend-Type-EntitiesDetectionJobProperties-JobId"></a>
The identifier assigned to the entities detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobName**   <a name="comprehend-Type-EntitiesDetectionJobProperties-JobName"></a>
The name that you assigned the entities detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-EntitiesDetectionJobProperties-JobStatus"></a>
The current status of the entities detection job\. If the status is `FAILED`, the `Message` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **LanguageCode**   <a name="comprehend-Type-EntitiesDetectionJobProperties-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 **Message**   <a name="comprehend-Type-EntitiesDetectionJobProperties-Message"></a>
A description of the status of a job\.  
Type: String  
Required: No

 **OutputDataConfig**   <a name="comprehend-Type-EntitiesDetectionJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the entities detection job\.   
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 **SubmitTime**   <a name="comprehend-Type-EntitiesDetectionJobProperties-SubmitTime"></a>
The time that the entities detection job was submitted for processing\.  
Type: Timestamp  
Required: No

 **VolumeKmsKeyId**   <a name="comprehend-Type-EntitiesDetectionJobProperties-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Required: No

 **VpcConfig**   <a name="comprehend-Type-EntitiesDetectionJobProperties-VpcConfig"></a>
 Configuration parameters for a private Virtual Private Cloud \(VPC\) containing the resources you are using for your entity detection job\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## See Also<a name="API_EntitiesDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntitiesDetectionJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntitiesDetectionJobProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/EntitiesDetectionJobProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntitiesDetectionJobProperties) 