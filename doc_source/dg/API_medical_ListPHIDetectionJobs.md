# ListPHIDetectionJobs<a name="API_medical_ListPHIDetectionJobs"></a>

Gets a list of protected health information \(PHI\) detection jobs that you have submitted\.

## Request Syntax<a name="API_medical_ListPHIDetectionJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-medical_ListPHIDetectionJobs-request-Filter)": { 
      "[JobName](API_medical_ComprehendMedicalAsyncJobFilter.md#comprehend-Type-medical_ComprehendMedicalAsyncJobFilter-JobName)": "string",
      "[JobStatus](API_medical_ComprehendMedicalAsyncJobFilter.md#comprehend-Type-medical_ComprehendMedicalAsyncJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_medical_ComprehendMedicalAsyncJobFilter.md#comprehend-Type-medical_ComprehendMedicalAsyncJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_medical_ComprehendMedicalAsyncJobFilter.md#comprehend-Type-medical_ComprehendMedicalAsyncJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-medical_ListPHIDetectionJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-medical_ListPHIDetectionJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_medical_ListPHIDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_medical_ListPHIDetectionJobs_RequestSyntax) **   <a name="comprehend-medical_ListPHIDetectionJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs based on their names, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [ComprehendMedicalAsyncJobFilter](API_medical_ComprehendMedicalAsyncJobFilter.md) object  
Required: No

 ** [MaxResults](#API_medical_ListPHIDetectionJobs_RequestSyntax) **   <a name="comprehend-medical_ListPHIDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_medical_ListPHIDetectionJobs_RequestSyntax) **   <a name="comprehend-medical_ListPHIDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_medical_ListPHIDetectionJobs_ResponseSyntax"></a>

```
{
   "[ComprehendMedicalAsyncJobPropertiesList](#comprehend-medical_ListPHIDetectionJobs-response-ComprehendMedicalAsyncJobPropertiesList)": [ 
      { 
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
   ],
   "[NextToken](#comprehend-medical_ListPHIDetectionJobs-response-NextToken)": "string"
}
```

## Response Elements<a name="API_medical_ListPHIDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ComprehendMedicalAsyncJobPropertiesList](#API_medical_ListPHIDetectionJobs_ResponseSyntax) **   <a name="comprehend-medical_ListPHIDetectionJobs-response-ComprehendMedicalAsyncJobPropertiesList"></a>
A list containing the properties of each job returned\.  
Type: Array of [ComprehendMedicalAsyncJobProperties](API_medical_ComprehendMedicalAsyncJobProperties.md) objects

 ** [NextToken](#API_medical_ListPHIDetectionJobs_ResponseSyntax) **   <a name="comprehend-medical_ListPHIDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_medical_ListPHIDetectionJobs_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
 An internal server error occurred\. Retry your request\.   
HTTP Status Code: 500

 **InvalidRequestException**   
 The request that you made is invalid\. Check your request to determine why it's invalid and then retry the request\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\. Contact customer support for more information about a service limit increase\.   
HTTP Status Code: 400

 **ValidationException**   
The filter that you specified for the operation is invalid\. Check the filter values that you entered and try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_medical_ListPHIDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/ListPHIDetectionJobs) 