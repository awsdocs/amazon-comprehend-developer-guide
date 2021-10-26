# DescribePiiEntitiesDetectionJob<a name="API_DescribePiiEntitiesDetectionJob"></a>

Gets the properties associated with a PII entities detection job\. For example, you can use this operation to get the job status\.

## Request Syntax<a name="API_DescribePiiEntitiesDetectionJob_RequestSyntax"></a>

```
{
   "JobId": "string"
}
```

## Request Parameters<a name="API_DescribePiiEntitiesDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ JobId ](#API_DescribePiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-DescribePiiEntitiesDetectionJob-request-JobId"></a>
The identifier that Amazon Comprehend generated for the job\. The [ StartPiiEntitiesDetectionJob ](API_StartPiiEntitiesDetectionJob.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_DescribePiiEntitiesDetectionJob_ResponseSyntax"></a>

```
{
   "PiiEntitiesDetectionJobProperties": { 
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
}
```

## Response Elements<a name="API_DescribePiiEntitiesDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ PiiEntitiesDetectionJobProperties ](#API_DescribePiiEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-DescribePiiEntitiesDetectionJob-response-PiiEntitiesDetectionJobProperties"></a>
Provides information about a PII entities detection job\.  
Type: [ PiiEntitiesDetectionJobProperties ](API_PiiEntitiesDetectionJobProperties.md) object

## Errors<a name="API_DescribePiiEntitiesDetectionJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** JobNotFoundException **   
The specified job was not found\. Check the job ID and try again\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribePiiEntitiesDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribePiiEntitiesDetectionJob) 