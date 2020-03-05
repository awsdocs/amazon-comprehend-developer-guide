# StartEntitiesDetectionJob<a name="API_StartEntitiesDetectionJob"></a>

Starts an asynchronous entity detection job for a collection of documents\. Use the [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md) operation to track the status of a job\.

This API can be used for either standard entity detection or custom entity recognition\. In order to be used for custom entity recognition, the optional `EntityRecognizerArn` must be used in order to provide access to the recognizer being used to detect the custom entity\.

## Request Syntax<a name="API_StartEntitiesDetectionJob_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-StartEntitiesDetectionJob-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-StartEntitiesDetectionJob-request-DataAccessRoleArn)": "string",
   "[EntityRecognizerArn](#comprehend-StartEntitiesDetectionJob-request-EntityRecognizerArn)": "string",
   "[InputDataConfig](#comprehend-StartEntitiesDetectionJob-request-InputDataConfig)": { 
      "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
      "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
   },
   "[JobName](#comprehend-StartEntitiesDetectionJob-request-JobName)": "string",
   "[LanguageCode](#comprehend-StartEntitiesDetectionJob-request-LanguageCode)": "string",
   "[OutputDataConfig](#comprehend-StartEntitiesDetectionJob-request-OutputDataConfig)": { 
      "[KmsKeyId](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-KmsKeyId)": "string",
      "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
   },
   "[VolumeKmsKeyId](#comprehend-StartEntitiesDetectionJob-request-VolumeKmsKeyId)": "string",
   "[VpcConfig](#comprehend-StartEntitiesDetectionJob-request-VpcConfig)": { 
      "[SecurityGroupIds](API_VpcConfig.md#comprehend-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
      "[Subnets](API_VpcConfig.md#comprehend-Type-VpcConfig-Subnets)": [ "string" ]
   }
}
```

## Request Parameters<a name="API_StartEntitiesDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-ClientRequestToken"></a>
A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\. For more information, see [https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions.html#auth-role-permissions](https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions.html#auth-role-permissions)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [EntityRecognizerArn](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the specific entity recognizer to be used by the `StartEntitiesDetectionJob`\. This ARN is optional and is only used for a custom entity recognition job\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 ** [InputDataConfig](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-JobName"></a>
The identifier of the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [LanguageCode](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-LanguageCode"></a>
The language of the input documents\. All documents must be in the same language\. You can specify any of the languages supported by Amazon Comprehend\. If custom entities recognition is used, this parameter is ignored and the language used for training the model is used instead\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [OutputDataConfig](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-OutputDataConfig"></a>
Specifies where to send the output files\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

 ** [VolumeKmsKeyId](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Required: No

 ** [VpcConfig](#API_StartEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-request-VpcConfig"></a>
Configuration parameters for an optional private Virtual Private Cloud \(VPC\) containing the resources you are using for your entity detection job\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## Response Syntax<a name="API_StartEntitiesDetectionJob_ResponseSyntax"></a>

```
{
   "[JobId](#comprehend-StartEntitiesDetectionJob-response-JobId)": "string",
   "[JobStatus](#comprehend-StartEntitiesDetectionJob-response-JobStatus)": "string"
}
```

## Response Elements<a name="API_StartEntitiesDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_StartEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-response-JobId"></a>
The identifier generated for the job\. To get the status of job, use this identifier with the [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md) operation\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [JobStatus](#API_StartEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StartEntitiesDetectionJob-response-JobStatus"></a>
The status of the job\.   
+ SUBMITTED \- The job has been received and is queued for processing\.
+ IN\_PROGRESS \- Amazon Comprehend is processing the job\.
+ COMPLETED \- The job was successfully completed and the output is available\.
+ FAILED \- The job did not complete\. To get details, use the [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md) operation\.
+ STOP\_REQUESTED \- Amazon Comprehend has received a stop request for the job and is processing the request\.
+ STOPPED \- The job was successfully stopped without completing\.
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartEntitiesDetectionJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **KmsKeyValidationException**   
The KMS customer managed key \(CMK\) entered cannot be validated\. Verify the key and re\-enter it\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **ResourceUnavailableException**   
The specified resource is not available\. Check to see if the resource is in the `TRAINED` state and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_StartEntitiesDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StartEntitiesDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StartEntitiesDetectionJob) 