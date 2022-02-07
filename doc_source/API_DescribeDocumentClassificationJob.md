# DescribeDocumentClassificationJob<a name="API_DescribeDocumentClassificationJob"></a>

Gets the properties associated with a document classification job\. Use this operation to get the status of a classification job\.

## Request Syntax<a name="API_DescribeDocumentClassificationJob_RequestSyntax"></a>

```
{
   "JobId": "string"
}
```

## Request Parameters<a name="API_DescribeDocumentClassificationJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_DescribeDocumentClassificationJob_RequestSyntax) **   <a name="comprehend-DescribeDocumentClassificationJob-request-JobId"></a>
The identifier that Amazon Comprehend generated for the job\. The [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) operation returns this identifier in its response\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_DescribeDocumentClassificationJob_ResponseSyntax"></a>

```
{
   "DocumentClassificationJobProperties": { 
      "DataAccessRoleArn": "string",
      "DocumentClassifierArn": "string",
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
}
```

## Response Elements<a name="API_DescribeDocumentClassificationJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DocumentClassificationJobProperties](#API_DescribeDocumentClassificationJob_ResponseSyntax) **   <a name="comprehend-DescribeDocumentClassificationJob-response-DocumentClassificationJobProperties"></a>
An object that describes the properties associated with the document classification job\.  
Type: [DocumentClassificationJobProperties](API_DocumentClassificationJobProperties.md) object

## Errors<a name="API_DescribeDocumentClassificationJob_Errors"></a>

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

## See Also<a name="API_DescribeDocumentClassificationJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeDocumentClassificationJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeDocumentClassificationJob) 