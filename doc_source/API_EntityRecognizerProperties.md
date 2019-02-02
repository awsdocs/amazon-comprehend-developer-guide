# EntityRecognizerProperties<a name="API_EntityRecognizerProperties"></a>

Describes information about an entity recognizer\.

## Contents<a name="API_EntityRecognizerProperties_Contents"></a>

 **DataAccessRoleArn**   <a name="comprehend-Type-EntityRecognizerProperties-DataAccessRoleArn"></a>
 The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **EndTime**   <a name="comprehend-Type-EntityRecognizerProperties-EndTime"></a>
The time that the recognizer creation completed\.  
Type: Timestamp  
Required: No

 **EntityRecognizerArn**   <a name="comprehend-Type-EntityRecognizerProperties-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 **InputDataConfig**   <a name="comprehend-Type-EntityRecognizerProperties-InputDataConfig"></a>
The input data properties of an entity recognizer\.  
Type: [EntityRecognizerInputDataConfig](API_EntityRecognizerInputDataConfig.md) object  
Required: No

 **LanguageCode**   <a name="comprehend-Type-EntityRecognizerProperties-LanguageCode"></a>
 The language of the input documents\. All documents must be in the same language\. Only English \("en"\) is currently supported\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: No

 **Message**   <a name="comprehend-Type-EntityRecognizerProperties-Message"></a>
 A description of the status of the recognizer\.  
Type: String  
Required: No

 **RecognizerMetadata**   <a name="comprehend-Type-EntityRecognizerProperties-RecognizerMetadata"></a>
 Provides information about an entity recognizer\.  
Type: [EntityRecognizerMetadata](API_EntityRecognizerMetadata.md) object  
Required: No

 **Status**   <a name="comprehend-Type-EntityRecognizerProperties-Status"></a>
Provides the status of the entity recognizer\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 **SubmitTime**   <a name="comprehend-Type-EntityRecognizerProperties-SubmitTime"></a>
The time that the recognizer was submitted for processing\.  
Type: Timestamp  
Required: No

 **TrainingEndTime**   <a name="comprehend-Type-EntityRecognizerProperties-TrainingEndTime"></a>
The time that training of the entity recognizer was completed\.  
Type: Timestamp  
Required: No

 **TrainingStartTime**   <a name="comprehend-Type-EntityRecognizerProperties-TrainingStartTime"></a>
The time that training of the entity recognizer started\.  
Type: Timestamp  
Required: No

## See Also<a name="API_EntityRecognizerProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/EntityRecognizerProperties) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/EntityRecognizerProperties) 