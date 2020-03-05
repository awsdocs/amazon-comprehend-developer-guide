# DescribePHIDetectionJob<a name="API_medical_DescribePHIDetectionJob"></a>

Gets the properties associated with a protected health information \(PHI\) detection job\. Use this operation to get the status of a detection job\.

## Request Syntax<a name="API_medical_DescribePHIDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-medical_DescribePHIDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_medical_DescribePHIDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_medical_DescribePHIDetectionJob_RequestSyntax) **   <a name="comprehend-medical_DescribePHIDetectionJob-request-JobId"></a>
The identifier that Amazon Comprehend Medical generated for the job\. The `StartPHIDetectionJob` operation returns this identifier in its response\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_medical_DescribePHIDetectionJob_ResponseSyntax"></a>

```
{
   "[ComprehendMedicalAsyncJobProperties](#comprehend-medical_DescribePHIDetectionJob-response-ComprehendMedicalAsyncJobProperties)": { 
      "[DataAccessRoleArn](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-DataAccessRoleArn)": "string",
      "[EndTime](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-EndTime)": number,
      "[ExpirationTime](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ExpirationTime)": number,
      "[InputDataConfig](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-InputDataConfig)": { 
         "[S3Bucket](API_medical_InputDataConfig.md#comprehend-Type-medical_InputDataConfig-S3Bucket)": "string",
         "[S3Key](API_medical_InputDataConfig.md#comprehend-Type-medical_InputDataConfig-S3Key)": "string"
      },
      "[JobId](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobId)": "string",
      "[JobName](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobName)": "string",
      "[JobStatus](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobStatus)": "string",
      "[KMSKey](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-KMSKey)": "string",
      "[LanguageCode](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-LanguageCode)": "string",
      "[ManifestFilePath](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ManifestFilePath)": "string",
      "[Message](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-Message)": "string",
      "[ModelVersion](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ModelVersion)": "string",
      "[OutputDataConfig](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-OutputDataConfig)": { 
         "[S3Bucket](API_medical_OutputDataConfig.md#comprehend-Type-medical_OutputDataConfig-S3Bucket)": "string",
         "[S3Key](API_medical_OutputDataConfig.md#comprehend-Type-medical_OutputDataConfig-S3Key)": "string"
      },
      "[SubmitTime](API_medical_ComprehendMedicalAsyncJobProperties.md#comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-SubmitTime)": number
   }
}
```

## Response Elements<a name="API_medical_DescribePHIDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ComprehendMedicalAsyncJobProperties](#API_medical_DescribePHIDetectionJob_ResponseSyntax) **   <a name="comprehend-medical_DescribePHIDetectionJob-response-ComprehendMedicalAsyncJobProperties"></a>
An object that contains the properties associated with a detection job\.  
Type: [ComprehendMedicalAsyncJobProperties](API_medical_ComprehendMedicalAsyncJobProperties.md) object

## Errors<a name="API_medical_DescribePHIDetectionJob_Errors"></a>

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

## See Also<a name="API_medical_DescribePHIDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/DescribePHIDetectionJob) 