# StartTopicsDetectionJob<a name="API_StartTopicsDetectionJob"></a>

Starts an asynchronous topic detection job\. Use the `DescribeTopicDetectionJob` operation to track the status of a job\.

## Request Syntax<a name="API_StartTopicsDetectionJob_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-StartTopicsDetectionJob-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-StartTopicsDetectionJob-request-DataAccessRoleArn)": "string",
   "[InputDataConfig](#comprehend-StartTopicsDetectionJob-request-InputDataConfig)": { 
      "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
      "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
   },
   "[JobName](#comprehend-StartTopicsDetectionJob-request-JobName)": "string",
   "[NumberOfTopics](#comprehend-StartTopicsDetectionJob-request-NumberOfTopics)": number,
   "[OutputDataConfig](#comprehend-StartTopicsDetectionJob-request-OutputDataConfig)": { 
      "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
   }
}
```

## Request Parameters<a name="API_StartTopicsDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-ClientRequestToken"></a>
A unique identifier for the request\. If you do not set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.   
Type: String  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-JobName"></a>
The identifier of the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [NumberOfTopics](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-NumberOfTopics"></a>
The number of topics to detect\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 100\.  
Required: No

 ** [OutputDataConfig](#API_StartTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-StartTopicsDetectionJob-request-OutputDataConfig"></a>
Specifies where to send the output files\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

## Response Syntax<a name="API_StartTopicsDetectionJob_ResponseSyntax"></a>

```
{
   "[JobId](#comprehend-StartTopicsDetectionJob-response-JobId)": "string",
   "[JobStatus](#comprehend-StartTopicsDetectionJob-response-JobStatus)": "string"
}
```

## Response Elements<a name="API_StartTopicsDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobId](#API_StartTopicsDetectionJob_ResponseSyntax) **   <a name="comprehend-StartTopicsDetectionJob-response-JobId"></a>
The identifier generated for the job\. To get the status of the job, use this identifier with the `DescribeTopicDetectionJob` operation\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.

 ** [JobStatus](#API_StartTopicsDetectionJob_ResponseSyntax) **   <a name="comprehend-StartTopicsDetectionJob-response-JobStatus"></a>
The status of the job:   

+ SUBMITTED \- The job has been received and is queued for processing\.

+ IN\_PROGRESS \- Amazon Comprehend is processing the job\.

+ COMPLETED \- The job was successfully completed and the output is available\.

+ FAILED \- The job did not complete\. To get details, use the `DescribeTopicDetectionJob` operation\.
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED` 

## Errors<a name="API_StartTopicsDetectionJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_StartTopicsDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StartTopicsDetectionJob) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/StartTopicsDetectionJob) 