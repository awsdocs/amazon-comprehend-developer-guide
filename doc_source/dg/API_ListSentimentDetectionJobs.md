# ListSentimentDetectionJobs<a name="API_ListSentimentDetectionJobs"></a>

Gets a list of sentiment detection jobs that you have submitted\.

## Request Syntax<a name="API_ListSentimentDetectionJobs_RequestSyntax"></a>

```
{
   "[Filter](#comprehend-ListSentimentDetectionJobs-request-Filter)": { 
      "[JobName](API_SentimentDetectionJobFilter.md#comprehend-Type-SentimentDetectionJobFilter-JobName)": "string",
      "[JobStatus](API_SentimentDetectionJobFilter.md#comprehend-Type-SentimentDetectionJobFilter-JobStatus)": "string",
      "[SubmitTimeAfter](API_SentimentDetectionJobFilter.md#comprehend-Type-SentimentDetectionJobFilter-SubmitTimeAfter)": number,
      "[SubmitTimeBefore](API_SentimentDetectionJobFilter.md#comprehend-Type-SentimentDetectionJobFilter-SubmitTimeBefore)": number
   },
   "[MaxResults](#comprehend-ListSentimentDetectionJobs-request-MaxResults)": number,
   "[NextToken](#comprehend-ListSentimentDetectionJobs-request-NextToken)": "string"
}
```

## Request Parameters<a name="API_ListSentimentDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListSentimentDetectionJobs_RequestSyntax) **   <a name="comprehend-ListSentimentDetectionJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [SentimentDetectionJobFilter](API_SentimentDetectionJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListSentimentDetectionJobs_RequestSyntax) **   <a name="comprehend-ListSentimentDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListSentimentDetectionJobs_RequestSyntax) **   <a name="comprehend-ListSentimentDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListSentimentDetectionJobs_ResponseSyntax"></a>

```
{
   "[NextToken](#comprehend-ListSentimentDetectionJobs-response-NextToken)": "string",
   "[SentimentDetectionJobPropertiesList](#comprehend-ListSentimentDetectionJobs-response-SentimentDetectionJobPropertiesList)": [ 
      { 
         "[DataAccessRoleArn](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-DataAccessRoleArn)": "string",
         "[EndTime](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-EndTime)": number,
         "[InputDataConfig](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-InputDataConfig)": { 
            "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
            "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
         },
         "[JobId](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-JobId)": "string",
         "[JobName](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-JobName)": "string",
         "[JobStatus](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-JobStatus)": "string",
         "[LanguageCode](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-LanguageCode)": "string",
         "[Message](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-Message)": "string",
         "[OutputDataConfig](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-OutputDataConfig)": { 
            "[KmsKeyId](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-KmsKeyId)": "string",
            "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
         },
         "[SubmitTime](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-SubmitTime)": number,
         "[VolumeKmsKeyId](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-VolumeKmsKeyId)": "string",
         "[VpcConfig](API_SentimentDetectionJobProperties.md#comprehend-Type-SentimentDetectionJobProperties-VpcConfig)": { 
            "[SecurityGroupIds](API_VpcConfig.md#comprehend-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
            "[Subnets](API_VpcConfig.md#comprehend-Type-VpcConfig-Subnets)": [ "string" ]
         }
      }
   ]
}
```

## Response Elements<a name="API_ListSentimentDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [NextToken](#API_ListSentimentDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListSentimentDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

 ** [SentimentDetectionJobPropertiesList](#API_ListSentimentDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListSentimentDetectionJobs-response-SentimentDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [SentimentDetectionJobProperties](API_SentimentDetectionJobProperties.md) objects

## Errors<a name="API_ListSentimentDetectionJobs_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidFilterException**   
The filter specified for the operation is invalid\. Specify a different filter\.  
HTTP Status Code: 400

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListSentimentDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListSentimentDetectionJobs) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListSentimentDetectionJobs) 