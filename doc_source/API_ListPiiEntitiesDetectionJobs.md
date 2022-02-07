# ListPiiEntitiesDetectionJobs<a name="API_ListPiiEntitiesDetectionJobs"></a>

Gets a list of the PII entity detection jobs that you have submitted\.

## Request Syntax<a name="API_ListPiiEntitiesDetectionJobs_RequestSyntax"></a>

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

## Request Parameters<a name="API_ListPiiEntitiesDetectionJobs_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Filter](#API_ListPiiEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListPiiEntitiesDetectionJobs-request-Filter"></a>
Filters the jobs that are returned\. You can filter jobs on their name, status, or the date and time that they were submitted\. You can only set one filter at a time\.  
Type: [PiiEntitiesDetectionJobFilter](API_PiiEntitiesDetectionJobFilter.md) object  
Required: No

 ** [MaxResults](#API_ListPiiEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListPiiEntitiesDetectionJobs-request-MaxResults"></a>
The maximum number of results to return in each page\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [NextToken](#API_ListPiiEntitiesDetectionJobs_RequestSyntax) **   <a name="comprehend-ListPiiEntitiesDetectionJobs-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListPiiEntitiesDetectionJobs_ResponseSyntax"></a>

```
{
   "NextToken": "string",
   "PiiEntitiesDetectionJobPropertiesList": [ 
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
         "LanguageCode": "string",
         "Message": "string",
         "Mode": "string",
         "OutputDataConfig": { 
            "KmsKeyId": "string",
            "S3Uri": "string"
         },
         "RedactionConfig": { 
            "MaskCharacter": "string",
            "MaskMode": "string",
            "PiiEntityTypes": [ "string" ]
         },
         "SubmitTime": number
      }
   ]
}
```

## Response Elements<a name="API_ListPiiEntitiesDetectionJobs_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [NextToken](#API_ListPiiEntitiesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListPiiEntitiesDetectionJobs-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

 ** [PiiEntitiesDetectionJobPropertiesList](#API_ListPiiEntitiesDetectionJobs_ResponseSyntax) **   <a name="comprehend-ListPiiEntitiesDetectionJobs-response-PiiEntitiesDetectionJobPropertiesList"></a>
A list containing the properties of each job that is returned\.  
Type: Array of [PiiEntitiesDetectionJobProperties](API_PiiEntitiesDetectionJobProperties.md) objects

## Errors<a name="API_ListPiiEntitiesDetectionJobs_Errors"></a>

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

## See Also<a name="API_ListPiiEntitiesDetectionJobs_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListPiiEntitiesDetectionJobs) 