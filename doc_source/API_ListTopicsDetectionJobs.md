# ListTopicsDetectionJobs<a name="API_ListTopicsDetectionJobs"></a>

Gets a list of the topic detection jobs that you have submitted\.

## Request Syntax<a name="API_ListTopicsDetectionJobs_RequestSyntax"></a>

```
{
   "Filter": { 
      "JobName": "string",
      "JobStatus": "string",
      "SubmitTimeAfter": number,
      "SubmitTimeBefore": number
   },
   "MaxResults": number,
   "NextToken": "string"
}
```

## Request Parameters<a name="API_ListTopicsDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see Common Parameters\.

The request accepts the following data in JSON format\.

 ** Filter **   
Filters the jobs that are returned\. Jobs can be filtered on their name, status, or the date and time that they were submitted\. You can set only one filter at a time\.  
Type: [TopicsDetectionJobFilter](API_TopicsDetectionJobFilter.md) object  
Required: No

 ** MaxResults **   
The maximum number of results to return in each page\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** NextToken **   
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListTopicsDetectionJobs_ResponseSyntax"></a>

```
{
   "NextToken": "string",
   "TopicsDetectionJobPropertiesList": [ 
      { 
         "EndTime": number,
         "InputDataConfig": { 
            "InputFormat": "string",
            "S3Uri": "string"
         },
         "JobId": "string",
         "JobName": "string",
         "JobStatus": "string",
         "Message": "string",
         "NumberOfTopics": number,
         "OutputDataConfig": { 
            "S3Uri": "string"
         },
         "SubmitTime": number
      }
   ]
}
```

## Response Elements<a name="API_ListTopicsDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** NextToken **   
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

 ** TopicsDetectionJobPropertiesList **   
A list containing the properties of each job that is returned\.  
Type: Array of [TopicsDetectionJobProperties](API_TopicsDetectionJobProperties.md) objects

## Errors<a name="API_ListTopicsDetectionJobs_Errors"></a>

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

## See Also<a name="API_ListTopicsDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListTopicsDetectionJobs) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/ListTopicsDetectionJobs) 