# EndpointProperties<a name="API_EndpointProperties"></a>

Specifies information about the specified endpoint\.

## Contents<a name="API_EndpointProperties_Contents"></a>

 ** CreationTime **   <a name="comprehend-Type-EndpointProperties-CreationTime"></a>
The creation date and time of the endpoint\.  
Type: Timestamp  
Required: No

 ** CurrentInferenceUnits **   <a name="comprehend-Type-EndpointProperties-CurrentInferenceUnits"></a>
The number of inference units currently used by the model using this endpoint\.  
Type: Integer  
Valid Range: Minimum value of 1\.  
Required: No

 ** DataAccessRoleArn **   <a name="comprehend-Type-EndpointProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to trained custom models encrypted with a customer managed key \(ModelKmsKeyId\)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** DesiredDataAccessRoleArn **   <a name="comprehend-Type-EndpointProperties-DesiredDataAccessRoleArn"></a>
Data access role ARN to use in case the new model is encrypted with a customer KMS key\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 ** DesiredInferenceUnits **   <a name="comprehend-Type-EndpointProperties-DesiredInferenceUnits"></a>
The desired number of inference units to be used by the model using this endpoint\. Each inference unit represents of a throughput of 100 characters per second\.  
Type: Integer  
Valid Range: Minimum value of 1\.  
Required: No

 ** DesiredModelArn **   <a name="comprehend-Type-EndpointProperties-DesiredModelArn"></a>
ARN of the new model to use for updating an existing endpoint\. This ARN is going to be different from the model ARN when the update is in progress  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** EndpointArn **   <a name="comprehend-Type-EndpointProperties-EndpointArn"></a>
The Amazon Resource Number \(ARN\) of the endpoint\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier-endpoint|entity-recognizer-endpoint)/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 ** LastModifiedTime **   <a name="comprehend-Type-EndpointProperties-LastModifiedTime"></a>
The date and time that the endpoint was last modified\.  
Type: Timestamp  
Required: No

 ** Message **   <a name="comprehend-Type-EndpointProperties-Message"></a>
Specifies a reason for failure in cases of `Failed` status\.  
Type: String  
Required: No

 ** ModelArn **   <a name="comprehend-Type-EndpointProperties-ModelArn"></a>
The Amazon Resource Number \(ARN\) of the model to which the endpoint is attached\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: No

 ** Status **   <a name="comprehend-Type-EndpointProperties-Status"></a>
Specifies the status of the endpoint\. Because the endpoint updates and creation are asynchronous, so customers will need to wait for the endpoint to be `Ready` status before making inference requests\.  
Type: String  
Valid Values:` CREATING | DELETING | FAILED | IN_SERVICE | UPDATING`   
Required: No

## See Also<a name="API_EndpointProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EndpointProperties) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EndpointProperties) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EndpointProperties) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EndpointProperties) 