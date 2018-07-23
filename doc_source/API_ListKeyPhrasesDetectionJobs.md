# ListKeyPhrasesDetectionJobs<a name="API_ListKeyPhrasesDetectionJobs"></a>

Get a list of key phrase detection jobs that you have submitted\.

## Request Syntax<a name="API_ListKeyPhrasesDetectionJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListKeyPhrasesDetectionJobs-request-Filter)": { 
      "[JobName](API_KeyPhrasesDetectionJobFilter.md#comprehend-Type-KeyPhrasesDetectionJobFilter-JobName)": "string",
      "[JobStatus](API_KeyPhrasesDetectionJobFilter.md#comprehend-Type-KeyPhrasesDetectionJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_KeyPhrasesDetectionJobFilter.md#comprehend-Type-KeyPhrasesDetectionJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_KeyPhrasesDetectionJobFilter.md#comprehend-Type-KeyPhrasesDetectionJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListKeyPhrasesDetectionJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-ListKeyPhrasesDetectionJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListKeyPhrasesDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListKeyPhrasesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListKeyPhrasesDetectionJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [KeyPhrasesDetectionJobFilter](API_KeyPhrasesDetectionJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListKeyPhrasesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListKeyPhrasesDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListKeyPhrasesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListKeyPhrasesDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListKeyPhrasesDetectionJobs_ResponseSyntax"></a>

```
{
   "[KeyPhrasesDetectionJobPropertiesList](#comprehend-ListKeyPhrasesDetectionJobs-response-KeyPhrasesDetectionJobPropertiesList)": [ 
      { 
         "[DataAccessRoleArn](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-DataAccessRoleArn)": "string",
         "[EndTime](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-EndTime)": number,
         "[InputDataConfig](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-InputDataConfig)": { 
            "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
            "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
         },
         "[JobId](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-JobId)": "string",
         "[JobName](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-JobName)": "string",
         "[JobStatus](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-JobStatus)": "string",
         "[LanguageCode](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-LanguageCode)": "string",
         "[Message](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-Message)": "string",
         "[OutputDataConfig](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-OutputDataConfig)": { 
            "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
         },
         "[SubmitTime](API_KeyPhrasesDetectionJobProperties.md#comprehend-Type-KeyPhrasesDetectionJobProperties-SubmitTime)": number
      }
   ],
   "[NextToken](#comprehend-ListKeyPhrasesDetectionJobs-response-NextToken)": "string"
}
```

## Response Elements<a name="API_ListKeyPhrasesDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [KeyPhrasesDetectionJobPropertiesList](#API_ListKeyPhrasesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListKeyPhrasesDetectionJobs-response-KeyPhrasesDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [KeyPhrasesDetectionJobProperties](API_KeyPhrasesDetectionJobProperties.md) objects

 ** [NextToken](#API_ListKeyPhrasesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListKeyPhrasesDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListKeyPhrasesDetectionJobs_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidFilterException**   
The filter specified for the `ListTopicDetectionJobs` operation is invalid\. Specify a different filter\.  
HTTP Status Code: 400

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListKeyPhrasesDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListKeyPhrasesDetectionJobs) 