# EntityRecognizerProperties<a name="API_EntityRecognizerProperties"></a>

Describes information about an entity recognizer\.

## Contents<a name="API_EntityRecognizerProperties_Contents"></a>

 ** DataAccessRoleArn **   <a name="comprehend-Type-EntityRecognizerProperties-DataAccessRoleArn"></a>
 The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** EndTime **   <a name="comprehend-Type-EntityRecognizerProperties-EndTime"></a>
The time that the recognizer creation completed\.  
Type: Timestamp  
Required: No

 ** EntityRecognizerArn **   <a name="comprehend-Type-EntityRecognizerProperties-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** InputDataConfig **   <a name="comprehend-Type-EntityRecognizerProperties-InputDataConfig"></a>
The input data properties of an entity recognizer\.  
Type: [ EntityRecognizerInputDataConfig ](API_EntityRecognizerInputDataConfig.md) object  
Required: No

 ** LanguageCode **   <a name="comprehend-Type-EntityRecognizerProperties-LanguageCode"></a>
 The language of the input documents\. All documents must be in the same language\. Only English \("en"\) is currently supported\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 ** Message **   <a name="comprehend-Type-EntityRecognizerProperties-Message"></a>
 A description of the status of the recognizer\.  
Type: String  
Required: No

 ** ModelKmsKeyId **   <a name="comprehend-Type-EntityRecognizerProperties-ModelKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt trained custom models\. The ModelKmsKeyId can be either of the following formats:   
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `.*`   
Required: No

 ** RecognizerMetadata **   <a name="comprehend-Type-EntityRecognizerProperties-RecognizerMetadata"></a>
 Provides information about an entity recognizer\.  
Type: [ EntityRecognizerMetadata ](API_EntityRecognizerMetadata.md) object  
Required: No

 ** Status **   <a name="comprehend-Type-EntityRecognizerProperties-Status"></a>
Provides the status of the entity recognizer\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 ** SubmitTime **   <a name="comprehend-Type-EntityRecognizerProperties-SubmitTime"></a>
The time that the recognizer was submitted for processing\.  
Type: Timestamp  
Required: No

 ** TrainingEndTime **   <a name="comprehend-Type-EntityRecognizerProperties-TrainingEndTime"></a>
The time that training of the entity recognizer was completed\.  
Type: Timestamp  
Required: No

 ** TrainingStartTime **   <a name="comprehend-Type-EntityRecognizerProperties-TrainingStartTime"></a>
The time that training of the entity recognizer started\.  
Type: Timestamp  
Required: No

 ** VersionName **   <a name="comprehend-Type-EntityRecognizerProperties-VersionName"></a>
The version name you assigned to the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

 ** VolumeKmsKeyId **   <a name="comprehend-Type-EntityRecognizerProperties-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `.*`   
Required: No

 ** VpcConfig **   <a name="comprehend-Type-EntityRecognizerProperties-VpcConfig"></a>
 Configuration parameters for a private Virtual Private Cloud \(VPC\) containing the resources you are using for your custom entity recognizer\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [ VpcConfig ](API_VpcConfig.md) object  
Required: No

## See Also<a name="API_EntityRecognizerProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerProperties) 