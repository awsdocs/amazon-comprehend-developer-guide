# DescribeEntitiesDetectionJob<a name="API_DescribeEntitiesDetectionJob"></a>

Gets the properties associated with an entities detection job\. Use this operation to get the status of a detection job\.

## Request Syntax<a name="API_DescribeEntitiesDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-DescribeEntitiesDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_DescribeEntitiesDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_DescribeEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-DescribeEntitiesDetectionJob-request-JobId"></a>
The identifier that Amazon Comprehend generated for the job\. The [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Required: Yes

## Response Syntax<a name="API_DescribeEntitiesDetectionJob_ResponseSyntax"></a>

```
{
   "[EntitiesDetectionJobProperties](#comprehend-DescribeEntitiesDetectionJob-response-EntitiesDetectionJobProperties)": { 
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
}
```

## Response Elements<a name="API_DescribeEntitiesDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntitiesDetectionJobProperties](#API_DescribeEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-DescribeEntitiesDetectionJob-response-EntitiesDetectionJobProperties"></a>
An object that contains the properties associated with an entities detection job\.  
Type: [EntitiesDetectionJobProperties](API_EntitiesDetectionJobProperties.md) object

## Errors<a name="API_DescribeEntitiesDetectionJob_Errors"></a>

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

## See Also<a name="API_DescribeEntitiesDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DescribeEntitiesDetectionJob) 