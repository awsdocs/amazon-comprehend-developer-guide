# DeletePHIDetectionJob<a name="API_medical_DeletePHIDetectionJob"></a>

Deletes a protected health information \(PHI\) detection job\.

## Request Syntax<a name="API_medical_DeletePHIDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-medical_DeletePHIDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_medical_DeletePHIDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_medical_DeletePHIDetectionJob_RequestSyntax) **   <a name="comprehend-medical_DeletePHIDetectionJob-request-JobId"></a>
The identifier that Amazon Comprehend Medical generated for the job to be deleted\. The `StartPHIDetectionJob` operation returns this identifier in its response\.   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_medical_DeletePHIDetectionJob_ResponseSyntax"></a>

```
{
   "[JobId](#comprehend-medical_DeletePHIDetectionJob-response-JobId)": "string"
}
```

## Response Elements<a name="API_medical_DeletePHIDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_medical_DeletePHIDetectionJob_ResponseSyntax) **   <a name="comprehend-medical_DeletePHIDetectionJob-response-JobId"></a>
The identifier that Amazon Comprehend Medical generated for the job to be deleted\. The `StartPHIDetectionJob` operation returns this identifier in its response\.   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

## Errors<a name="API_medical_DeletePHIDetectionJob_Errors"></a>

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

## See Also<a name="API_medical_DeletePHIDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/DeletePHIDetectionJob) 