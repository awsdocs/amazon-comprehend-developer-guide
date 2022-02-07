# StartPiiEntitiesDetectionJob<a name="API_StartPiiEntitiesDetectionJob"></a>

Starts an asynchronous PII entity detection job for a collection of documents\.

## Request Syntax<a name="API_StartPiiEntitiesDetectionJob_RequestSyntax"></a>

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
   "Tags": [ 
      { 
         "Key": "string",
         "Value": "string"
      }
   ]
}
```

## Request Parameters<a name="API_StartPiiEntitiesDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-ClientRequestToken"></a>
A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-InputDataConfig"></a>
The input properties for a PII entities detection job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-JobName"></a>
The identifier of the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [LanguageCode](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-LanguageCode"></a>
The language of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [Mode](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-Mode"></a>
Specifies whether the output provides the locations \(offsets\) of PII entities or a file in which PII entities are redacted\.  
Type: String  
Valid Values:` ONLY_REDACTION | ONLY_OFFSETS`   
Required: Yes

 ** [OutputDataConfig](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-OutputDataConfig"></a>
Provides conﬁguration parameters for the output of PII entity detection jobs\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

 ** [RedactionConfig](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-RedactionConfig"></a>
Provides configuration parameters for PII entity redaction\.  
This parameter is required if you set the `Mode` parameter to `ONLY_REDACTION`\. In that case, you must provide a `RedactionConfig` definition that includes the `PiiEntityTypes` parameter\.  
Type: [RedactionConfig](API_RedactionConfig.md) object  
Required: No

 ** [Tags](#API_StartPiiEntitiesDetectionJob_RequestSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-request-Tags"></a>
Tags to be associated with the PII entities detection job\. A tag is a key\-value pair that adds metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.  
Type: Array of [Tag](API_Tag.md) objects  
Required: No

## Response Syntax<a name="API_StartPiiEntitiesDetectionJob_ResponseSyntax"></a>

```
{
   "JobArn": "string",
   "JobId": "string",
   "JobStatus": "string"
}
```

## Response Elements<a name="API_StartPiiEntitiesDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobArn](#API_StartPiiEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-response-JobArn"></a>
The Amazon Resource Name \(ARN\) of the PII entity detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:pii-entities-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:pii-entities-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?` 

 ** [JobId](#API_StartPiiEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-response-JobId"></a>
The identifier generated for the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [JobStatus](#API_StartPiiEntitiesDetectionJob_ResponseSyntax) **   <a name="comprehend-StartPiiEntitiesDetectionJob-response-JobStatus"></a>
The status of the job\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartPiiEntitiesDetectionJob_Errors"></a>

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

## See Also<a name="API_StartPiiEntitiesDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StartPiiEntitiesDetectionJob) 