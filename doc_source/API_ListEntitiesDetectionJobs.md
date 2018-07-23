# ListEntitiesDetectionJobs<a name="API_ListEntitiesDetectionJobs"></a>

Gets a list of the entity detection jobs that you have submitted\.

## Request Syntax<a name="API_ListEntitiesDetectionJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListEntitiesDetectionJobs-request-Filter)": { 
      "[JobName](API_EntitiesDetectionJobFilter.md#comprehend-Type-EntitiesDetectionJobFilter-JobName)": "string",
      "[JobStatus](API_EntitiesDetectionJobFilter.md#comprehend-Type-EntitiesDetectionJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_EntitiesDetectionJobFilter.md#comprehend-Type-EntitiesDetectionJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_EntitiesDetectionJobFilter.md#comprehend-Type-EntitiesDetectionJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListEntitiesDetectionJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-ListEntitiesDetectionJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListEntitiesDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListEntitiesDetectionJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [EntitiesDetectionJobFilter](API_EntitiesDetectionJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListEntitiesDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListEntitiesDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListEntitiesDetectionJobs_ResponseSyntax"></a>

```
{
   "[EntitiesDetectionJobPropertiesList](#comprehend-ListEntitiesDetectionJobs-response-EntitiesDetectionJobPropertiesList)": [ 
      { 
         "[DataAccessRoleArn](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-DataAccessRoleArn)": "string",
         "[EndTime](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-EndTime)": number,
         "[InputDataConfig](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-InputDataConfig)": { 
            "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
            "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
         },
         "[JobId](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-JobId)": "string",
         "[JobName](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-JobName)": "string",
         "[JobStatus](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-JobStatus)": "string",
         "[LanguageCode](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-LanguageCode)": "string",
         "[Message](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-Message)": "string",
         "[OutputDataConfig](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-OutputDataConfig)": { 
            "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
         },
         "[SubmitTime](API_EntitiesDetectionJobProperties.md#comprehend-Type-EntitiesDetectionJobProperties-SubmitTime)": number
      }
   ],
   "[NextToken](#comprehend-ListEntitiesDetectionJobs-response-NextToken)": "string"
}
```

## Response Elements<a name="API_ListEntitiesDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntitiesDetectionJobPropertiesList](#API_ListEntitiesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListEntitiesDetectionJobs-response-EntitiesDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [EntitiesDetectionJobProperties](API_EntitiesDetectionJobProperties.md) objects

 ** [NextToken](#API_ListEntitiesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListEntitiesDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListEntitiesDetectionJobs_Errors"></a>

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

## See Also<a name="API_ListEntitiesDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListEntitiesDetectionJobs) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListEntitiesDetectionJobs) 