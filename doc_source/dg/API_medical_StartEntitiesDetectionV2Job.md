# StartEntitiesDetectionV2Job<a name="API_medical_StartEntitiesDetectionV2Job"></a>

Starts an asynchronous medical entity detection job for a collection of documents\. Use the `DescribeEntitiesDetectionV2Job` operation to track the status of a job\.

## Request Syntax<a name="API_medical_StartEntitiesDetectionV2Job_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-medical_StartEntitiesDetectionV2Job-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-medical_StartEntitiesDetectionV2Job-request-DataAccessRoleArn)": "string",
   "[InputDataConfig](#comprehend-medical_StartEntitiesDetectionV2Job-request-InputDataConfig)": { 
      "[S3Bucket](API_medical_InputDataConfig.md#comprehend-Type-medical_InputDataConfig-S3Bucket)": "string",
      "[S3Key](API_medical_InputDataConfig.md#comprehend-Type-medical_InputDataConfig-S3Key)": "string"
   },
   "[JobName](#comprehend-medical_StartEntitiesDetectionV2Job-request-JobName)": "string",
   "[KMSKey](#comprehend-medical_StartEntitiesDetectionV2Job-request-KMSKey)": "string",
   "[LanguageCode](#comprehend-medical_StartEntitiesDetectionV2Job-request-LanguageCode)": "string",
   "[OutputDataConfig](#comprehend-medical_StartEntitiesDetectionV2Job-request-OutputDataConfig)": { 
      "[S3Bucket](API_medical_OutputDataConfig.md#comprehend-Type-medical_OutputDataConfig-S3Bucket)": "string",
      "[S3Key](API_medical_OutputDataConfig.md#comprehend-Type-medical_OutputDataConfig-S3Key)": "string"
   }
}
```

## Request Parameters<a name="API_medical_StartEntitiesDetectionV2Job_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-ClientRequestToken"></a>
A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend Medical generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend Medical read access to your input data\. For more information, see [ Role\-Based Permissions Required for Asynchronous Operations](https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions-med.html#auth-role-permissions-med)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [InputDataConfig](API_medical_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-JobName"></a>
The identifier of the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [KMSKey](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-KMSKey"></a>
An AWS Key Management Service key to encrypt your output files\. If you do not specify a key, the files are written in plain text\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 2048\.  
Pattern: `.*`   
Required: No

 ** [LanguageCode](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-LanguageCode"></a>
The language of the input documents\. All documents must be in the same language\.  
Type: String  
Valid Values:` en`   
Required: Yes

 ** [OutputDataConfig](#API_medical_StartEntitiesDetectionV2Job_RequestSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-request-OutputDataConfig"></a>
Specifies where to send the output files\.  
Type: [OutputDataConfig](API_medical_OutputDataConfig.md) object  
Required: Yes

## Response Syntax<a name="API_medical_StartEntitiesDetectionV2Job_ResponseSyntax"></a>

```
{
   "[JobId](#comprehend-medical_StartEntitiesDetectionV2Job-response-JobId)": "string"
}
```

## Response Elements<a name="API_medical_StartEntitiesDetectionV2Job_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_medical_StartEntitiesDetectionV2Job_ResponseSyntax) **   <a name="comprehend-medical_StartEntitiesDetectionV2Job-response-JobId"></a>
The identifier generated for the job\. To get the status of a job, use this identifier with the `DescribeEntitiesDetectionV2Job` operation\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

## Errors<a name="API_medical_StartEntitiesDetectionV2Job_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
 An internal server error occurred\. Retry your request\.   
HTTP Status Code: 500

 **InvalidRequestException**   
 The request that you made is invalid\. Check your request to determine why it's invalid and then retry the request\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The resource identified by the specified Amazon Resource Name \(ARN\) was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\. Contact customer support for more information about a service limit increase\.   
HTTP Status Code: 400

## See Also<a name="API_medical_StartEntitiesDetectionV2Job_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/StartEntitiesDetectionV2Job) 