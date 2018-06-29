# ListDominantLanguageDetectionJobs<a name="API_ListDominantLanguageDetectionJobs"></a>

Gets a list of the dominant language detection jobs that you have submitted\.

## Request Syntax<a name="API_ListDominantLanguageDetectionJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListDominantLanguageDetectionJobs-request-Filter)": { 
      "[JobName](API_DominantLanguageDetectionJobFilter.md#comprehend-Type-DominantLanguageDetectionJobFilter-JobName)": "string",
      "[JobStatus](API_DominantLanguageDetectionJobFilter.md#comprehend-Type-DominantLanguageDetectionJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_DominantLanguageDetectionJobFilter.md#comprehend-Type-DominantLanguageDetectionJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_DominantLanguageDetectionJobFilter.md#comprehend-Type-DominantLanguageDetectionJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListDominantLanguageDetectionJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-ListDominantLanguageDetectionJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListDominantLanguageDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-Filter"></a>
Filters that jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [DominantLanguageDetectionJobFilter](API_DominantLanguageDetectionJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListDominantLanguageDetectionJobs_ResponseSyntax"></a>

```
{
   "[DominantLanguageDetectionJobPropertiesList](#comprehend-ListDominantLanguageDetectionJobs-response-DominantLanguageDetectionJobPropertiesList)": [ 
      { 
         "[EndTime](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-EndTime)": number,
         "[InputDataConfig](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-InputDataConfig)": { 
            "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
            "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
         },
         "[JobId](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-JobId)": "string",
         "[JobName](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-JobName)": "string",
         "[JobStatus](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-JobStatus)": "string",
         "[Message](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-Message)": "string",
         "[OutputDataConfig](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-OutputDataConfig)": { 
            "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
         },
         "[SubmitTime](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-SubmitTime)": number
      }
   ],
   "[NextToken](#comprehend-ListDominantLanguageDetectionJobs-response-NextToken)": "string"
}
```

## Response Elements<a name="API_ListDominantLanguageDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DominantLanguageDetectionJobPropertiesList](#API_ListDominantLanguageDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-response-DominantLanguageDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [DominantLanguageDetectionJobProperties](API_DominantLanguageDetectionJobProperties.md) objects

 ** [NextToken](#API_ListDominantLanguageDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListDominantLanguageDetectionJobs_Errors"></a>

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

## See Also<a name="API_ListDominantLanguageDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 