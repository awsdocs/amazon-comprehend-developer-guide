# StartEventsDetectionJob<a name="API_StartEventsDetectionJob"></a>

Starts an asynchronous event detection job for a collection of documents\.

## Request Syntax<a name="API_StartEventsDetectionJob_RequestSyntax"></a>

```
{
   "ClientRequestToken": "string",
   "DataAccessRoleArn": "string",
   "InputDataConfig": { 
      "DocumentReaderConfig": { 
         "DocumentReadAction": "string",
         "DocumentReadMode": "string",
         "FeatureTypes": [ "string" ]
      },
      "InputFormat": "string",
      "S3Uri": "string"
   },
   "JobName": "string",
   "LanguageCode": "string",
   "OutputDataConfig": { 
      "KmsKeyId": "string",
      "S3Uri": "string"
   },
   "Tags": [ 
      { 
         "Key": "string",
         "Value": "string"
      }
   ],
   "TargetEventTypes": [ "string" ]
}
```

## Request Parameters<a name="API_StartEventsDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ ClientRequestToken ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-ClientRequestToken"></a>
An unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [ DataAccessRoleArn ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [ InputDataConfig ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [ InputDataConfig ](API_InputDataConfig.md) object  
Required: Yes

 ** [ JobName ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-JobName"></a>
The identifier of the events detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [ LanguageCode ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [ OutputDataConfig ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-OutputDataConfig"></a>
Specifies where to send the output files\.  
Type: [ OutputDataConfig ](API_OutputDataConfig.md) object  
Required: Yes

 ** [ Tags ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-Tags"></a>
Tags to be associated with the events detection job\. A tag is a key\-value pair that adds metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.  
Type: Array of [ Tag ](API_Tag.md) objects  
Required: No

 ** [ TargetEventTypes ](#API_StartEventsDetectionJob_RequestSyntax) **   <a name="comprehend-StartEventsDetectionJob-request-TargetEventTypes"></a>
The types of events to detect in the input documents\.  
Type: Array of strings  
Array Members: Minimum number of 1 item\.  
Length Constraints: Minimum length of 1\. Maximum length of 40\.  
Pattern: `[A-Z_]*`   
Required: Yes

## Response Syntax<a name="API_StartEventsDetectionJob_ResponseSyntax"></a>

```
{
   "JobArn": "string",
   "JobId": "string",
   "JobStatus": "string"
}
```

## Response Elements<a name="API_StartEventsDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ JobArn ](#API_StartEventsDetectionJob_ResponseSyntax) **   <a name="comprehend-StartEventsDetectionJob-response-JobArn"></a>
The Amazon Resource Name \(ARN\) of the events detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:events-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:events-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?` 

 ** [ JobId ](#API_StartEventsDetectionJob_ResponseSyntax) **   <a name="comprehend-StartEventsDetectionJob-response-JobId"></a>
An unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [ JobStatus ](#API_StartEventsDetectionJob_ResponseSyntax) **   <a name="comprehend-StartEventsDetectionJob-response-JobStatus"></a>
The status of the events detection job\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartEventsDetectionJob_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** KmsKeyValidationException **   
The KMS customer managed key \(CMK\) entered cannot be validated\. Verify the key and re\-enter it\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 ** TooManyTagsException **   
The request contains more tags than can be associated with a resource \(50 tags per resource\)\. The maximum number of tags includes both existing tags and those included in your current request\.   
HTTP Status Code: 400

## See Also<a name="API_StartEventsDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StartEventsDetectionJob) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StartEventsDetectionJob) 