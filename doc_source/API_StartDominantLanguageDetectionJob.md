# StartDominantLanguageDetectionJob<a name="API_StartDominantLanguageDetectionJob"></a>

Starts an asynchronous dominant language detection job for a collection of documents\. Use the [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md) operation to track the status of a job\.

## Request Syntax<a name="API_StartDominantLanguageDetectionJob_RequestSyntax"></a>

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
   "VolumeKmsKeyId": "string",
   "VpcConfig": { 
      "SecurityGroupIds": [ "string" ],
      "Subnets": [ "string" ]
   }
}
```

## Request Parameters<a name="API_StartDominantLanguageDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-ClientRequestToken"></a>
A unique identifier for the request\. If you do not set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that grants Amazon Comprehend read access to your input data\. For more information, see [https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions.html#auth-role-permissions](https://docs.aws.amazon.com/comprehend/latest/dg/access-control-managing-permissions.html#auth-role-permissions)\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [InputDataConfig](API_InputDataConfig.md) object  
Required: Yes

 ** [JobName](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-JobName"></a>
An identifier for the job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 ** [OutputDataConfig](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-OutputDataConfig"></a>
Specifies where to send the output files\.  
Type: [OutputDataConfig](API_OutputDataConfig.md) object  
Required: Yes

 ** [Tags](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-Tags"></a>
Tags to be associated with the dominant language detection job\. A tag is a key\-value pair that adds metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.  
Type: Array of [Tag](API_Tag.md) objects  
Required: No

 ** [VolumeKmsKeyId](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-VolumeKmsKeyId"></a>
ID for the AWS Key Management Service \(KMS\) key that Amazon Comprehend uses to encrypt data on the storage volume attached to the ML compute instance\(s\) that process the analysis job\. The VolumeKmsKeyId can be either of the following formats:  
+ KMS Key ID: `"1234abcd-12ab-34cd-56ef-1234567890ab"` 
+ Amazon Resource Name \(ARN\) of a KMS Key: `"arn:aws:kms:us-west-2:111122223333:key/1234abcd-12ab-34cd-56ef-1234567890ab"` 
Type: String  
Length Constraints: Maximum length of 2048\.  
Pattern: `^\p{ASCII}+$`   
Required: No

 ** [VpcConfig](#API_StartDominantLanguageDetectionJob_RequestSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-request-VpcConfig"></a>
Configuration parameters for an optional private Virtual Private Cloud \(VPC\) containing the resources you are using for your dominant language detection job\. For more information, see [Amazon VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)\.   
Type: [VpcConfig](API_VpcConfig.md) object  
Required: No

## Response Syntax<a name="API_StartDominantLanguageDetectionJob_ResponseSyntax"></a>

```
{
   "JobArn": "string",
   "JobId": "string",
   "JobStatus": "string"
}
```

## Response Elements<a name="API_StartDominantLanguageDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [JobArn](#API_StartDominantLanguageDetectionJob_ResponseSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-response-JobArn"></a>
The Amazon Resource Name \(ARN\) of the dominant language detection job\. It is a unique, fully qualified identifier for the job\. It includes the AWS account, Region, and the job ID\. The format of the ARN is as follows:  
 `arn:<partition>:comprehend:<region>:<account-id>:dominant-language-detection-job/<job-id>`   
The following is an example job ARN:  
 `arn:aws:comprehend:us-west-2:111122223333:dominant-language-detection-job/1234abcd12ab34cd56ef1234567890ab`   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?` 

 ** [JobId](#API_StartDominantLanguageDetectionJob_ResponseSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-response-JobId"></a>
The identifier generated for the job\. To get the status of a job, use this identifier with the [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md) operation\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$` 

 ** [JobStatus](#API_StartDominantLanguageDetectionJob_ResponseSyntax) **   <a name="comprehend-StartDominantLanguageDetectionJob-response-JobStatus"></a>
The status of the job\.   
+ SUBMITTED \- The job has been received and is queued for processing\.
+ IN\_PROGRESS \- Amazon Comprehend is processing the job\.
+ COMPLETED \- The job was successfully completed and the output is available\.
+ FAILED \- The job did not complete\. To get details, use the [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md) operation\.
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | FAILED | STOP_REQUESTED | STOPPED` 

## Errors<a name="API_StartDominantLanguageDetectionJob_Errors"></a>

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

## See Also<a name="API_StartDominantLanguageDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StartDominantLanguageDetectionJob) 