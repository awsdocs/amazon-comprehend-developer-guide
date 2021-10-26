# ListDominantLanguageDetectionJobs<a name="API_ListDominantLanguageDetectionJobs"></a>

Gets a list of the dominant language detection jobs that you have submitted\.

## Request Syntax<a name="API_ListDominantLanguageDetectionJobs_RequestSyntax"></a>

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

## Request Parameters<a name="API_ListDominantLanguageDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ Filter ](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-Filter"></a>
Filters that jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [ DominantLanguageDetectionJobFilter ](API_DominantLanguageDetectionJobFilter.md) object  
Required: No

 ** [ MaxResults ](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [ NextToken ](#API_ListDominantLanguageDetectionJobs_RequestSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListDominantLanguageDetectionJobs_ResponseSyntax"></a>

```
{
   "DominantLanguageDetectionJobPropertiesList": [ 
      { 
         "DataAccessRoleArn": "string",
         "EndTime": number,
         "InputDataConfig": { 
            "DocumentReaderConfig": { 
               "DocumentReadAction": "string",
               "DocumentReadMode": "string",
               "FeatureTypes": [ "string" ]
            },
            "InputFormat": "string",
            "S3Uri": "string"
         },
         "JobArn": "string",
         "JobId": "string",
         "JobName": "string",
         "JobStatus": "string",
         "Message": "string",
         "OutputDataConfig": { 
            "KmsKeyId": "string",
            "S3Uri": "string"
         },
         "SubmitTime": number,
         "VolumeKmsKeyId": "string",
         "VpcConfig": { 
            "SecurityGroupIds": [ "string" ],
            "Subnets": [ "string" ]
         }
      }
   ],
   "NextToken": "string"
}
```

## Response Elements<a name="API_ListDominantLanguageDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ DominantLanguageDetectionJobPropertiesList ](#API_ListDominantLanguageDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-response-DominantLanguageDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [ DominantLanguageDetectionJobProperties ](API_DominantLanguageDetectionJobProperties.md) objects

 ** [ NextToken ](#API_ListDominantLanguageDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListDominantLanguageDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListDominantLanguageDetectionJobs_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidFilterException **   
The filter specified for the operation is invalid\. Specify a different filter\.  
HTTP Status Code: 400

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListDominantLanguageDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListDominantLanguageDetectionJobs) 