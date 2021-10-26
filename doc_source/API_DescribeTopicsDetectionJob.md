# DescribeTopicsDetectionJob<a name="API_DescribeTopicsDetectionJob"></a>

Gets the properties associated with a topic detection job\. Use this operation to get the status of a detection job\.

## Request Syntax<a name="API_DescribeTopicsDetectionJob_RequestSyntax"></a>

```
{
   "[JobId](#comprehend-DescribeTopicsDetectionJob-request-JobId)": "string"
}
```

## Request Parameters<a name="API_DescribeTopicsDetectionJob_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [JobId](#API_DescribeTopicsDetectionJob_RequestSyntax) **   <a name="comprehend-DescribeTopicsDetectionJob-request-JobId"></a>
The identifier assigned by the user to the detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: Yes

## Response Syntax<a name="API_DescribeTopicsDetectionJob_ResponseSyntax"></a>

```
{
   "[TopicsDetectionJobProperties](#comprehend-DescribeTopicsDetectionJob-response-TopicsDetectionJobProperties)": { 
      "[DataAccessRoleArn](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-DataAccessRoleArn)": "string",
      "[EndTime](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-EndTime)": number,
      "[InputDataConfig](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-InputDataConfig)": { 
         "[InputFormat](API_InputDataConfig.md#comprehend-Type-InputDataConfig-InputFormat)": "string",
         "[S3Uri](API_InputDataConfig.md#comprehend-Type-InputDataConfig-S3Uri)": "string"
      },
      "[JobId](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-JobId)": "string",
      "[JobName](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-JobName)": "string",
      "[JobStatus](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-JobStatus)": "string",
      "[Message](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-Message)": "string",
      "[NumberOfTopics](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-NumberOfTopics)": number,
      "[OutputDataConfig](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-OutputDataConfig)": { 
         "[KmsKeyId](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-KmsKeyId)": "string",
         "[S3Uri](API_OutputDataConfig.md#comprehend-Type-OutputDataConfig-S3Uri)": "string"
      },
      "[SubmitTime](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-SubmitTime)": number,
      "[VolumeKmsKeyId](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-VolumeKmsKeyId)": "string",
      "[VpcConfig](API_TopicsDetectionJobProperties.md#comprehend-Type-TopicsDetectionJobProperties-VpcConfig)": { 
         "[SecurityGroupIds](API_VpcConfig.md#comprehend-Type-VpcConfig-SecurityGroupIds)": [ "string" ],
         "[Subnets](API_VpcConfig.md#comprehend-Type-VpcConfig-Subnets)": [ "string" ]
      }
   }
}
```

## Response Elements<a name="API_DescribeTopicsDetectionJob_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [TopicsDetectionJobProperties](#API_DescribeTopicsDetectionJob_ResponseSyntax) **   <a name="comprehend-DescribeTopicsDetectionJob-response-TopicsDetectionJobProperties"></a>
The list of properties for the requested job\.  
Type: [TopicsDetectionJobProperties](API_TopicsDetectionJobProperties.md) object

## Errors<a name="API_DescribeTopicsDetectionJob_Errors"></a>

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

## See Also<a name="API_DescribeTopicsDetectionJob_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeTopicsDetectionJob) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeTopicsDetectionJob) 