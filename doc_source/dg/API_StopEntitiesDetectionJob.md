# StopEntitiesDetectionJob<a name="API_StopEntitiesDetectionJob"></a>

Stops an entities detection job in progress\.

If the job state is `IN_PROGRESS` the job is marked for termination and put into the `STOP_REQUESTED` state\. If the job completes before it can be stopped, it is put into the `COMPLETED` state; otherwise the job is stopped and put into the `STOPPED` state\.

If the job is in the `COMPLETED` or `FAILED` state when you call the `StopDominantLanguageDetectionJob` operation, the operation returns a 400 Internal Request Exception\. 

When a job is stopped, any documents already processed are written to the output location\.

## Request Syntax<a name="API_StopEntitiesDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-StopEntitiesDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_StopEntitiesDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_StopEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StopEntitiesDetectionJob-request-JobId"></a>
The identifier of the entities detection job to stop\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_StopEntitiesDetectionJob_ResponseSyntax"></a>

```
{
   "[JobId](#comprehend-StopEntitiesDetectionJob-response-JobId)": "string",
   "[JobStatus](#comprehend-StopEntitiesDetectionJob-response-JobStatus)": "string"
}
```

## Response Elements<a name="API_StopEntitiesDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_StopEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StopEntitiesDetectionJob-response-JobId"></a>
The identifier of the entities detection job to stop\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [JobStatus](#API_StopEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StopEntitiesDetectionJob-response-JobStatus"></a>
Either `STOP_REQUESTED` if the job is currently running, or `STOPPED` if the job was previously stopped with the `StopEntitiesDetectionJob` operation\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StopEntitiesDetectionJob_Errors"></a>

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

## See Also<a name="API_StopEntitiesDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StopEntitiesDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StopEntitiesDetectionJob) 