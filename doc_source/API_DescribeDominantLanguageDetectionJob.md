# DescribeDominantLanguageDetectionJob<a name="API_DescribeDominantLanguageDetectionJob"></a>

Gets the properties associated with a dominant language detection job\. Use this operation to get the status of a detection job\.

## Request Syntax<a name="API_DescribeDominantLanguageDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-DescribeDominantLanguageDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_DescribeDominantLanguageDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_DescribeDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-DescribeDominantLanguageDetectionJob-request-JobId"></a>
The identifier that Amazon Comprehend generated for the job\. The [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_DescribeDominantLanguageDetectionJob_ResponseSyntax"></a>

```
{
   "[DominantLanguageDetectionJobProperties](#comprehend-DescribeDominantLanguageDetectionJob-response-DominantLanguageDetectionJobProperties)": { 
      "[DataAccessRoleArn](API_DominantLanguageDetectionJobProperties.md#comprehend-Type-DominantLanguageDetectionJobProperties-DataAccessRoleArn)": "string",
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
}
```

## Response Elements<a name="API_DescribeDominantLanguageDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DominantLanguageDetectionJobProperties](#API_DescribeDominantLanguageDetectionJob_ResponseSyntax) **   <a name="comprehend-DescribeDominantLanguageDetectionJob-response-DominantLanguageDetectionJobProperties"></a>
An object that contains the properties associated with a dominant language detection job\.  
Type: [DominantLanguageDetectionJobProperties](API_DominantLanguageDetectionJobProperties.md) object

## Errors<a name="API_DescribeDominantLanguageDetectionJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **JobNotFoundException**   
The specified job was not found\. Check the job ID and try again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeDominantLanguageDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DescribeDominantLanguageDetectionJob) 