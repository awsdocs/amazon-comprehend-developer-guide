# KeyPhrasesDetectionJobProperties<a name="API_KeyPhrasesDetectionJobProperties"></a>

Provides information about a key phrases detection job\.

## Contents<a name="API_KeyPhrasesDetectionJobProperties_Contents"></a>

 ** DataAccessRoleArn **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) that gives Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** EndTime **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-EndTime"></a>
The time that the key phrases detection job completed\.  
Type: Timestamp  
Required: No

 ** InputDataConfig **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the key phrases detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: No

 ** JobArn **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-JobArn"></a>
The Amazon Resource Name \(ARN\) of the key phrases detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:key-phrases-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:key-phrases-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** JobId **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-JobId"></a>
The identifier assigned to the key phrases detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobName **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-JobName"></a>
The name that you assigned the key phrases detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** JobStatus **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-JobStatus"></a>
The current status of the key phrases detection job\. If the status is `FAILED`, the `Message` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 ** LanguageCode **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 ** Message **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-Message"></a>
A description of the status of a job\.  
Type: String  
Required: No

 ** OutputDataConfig **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the key phrases detection job\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: No

 ** SubmitTime **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-SubmitTime"></a>
The time that the key phrases detection job was submitted for processing\.  
Type: Timestamp  
Required: No

 ** VolumeKmsKeyId **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `^\p{ASCII}+$`   
Required: No

 ** VpcConfig **   <a name="comprehend-Type-KeyPhrasesDetectionJobProperties-VpcConfig"></a>
 Configuration parameters for a private Virtual Private Cloud \(VPC\) containing the resources you are using for your key phrases detection job\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## See Also<a name="API_KeyPhrasesDetectionJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/KeyPhrasesDetectionJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/KeyPhrasesDetectionJobProperties) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/KeyPhrasesDetectionJobProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/KeyPhrasesDetectionJobProperties) 