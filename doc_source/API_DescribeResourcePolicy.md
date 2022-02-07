# DescribeResourcePolicy<a name="API_DescribeResourcePolicy"></a>

Gets the details of a resource\-based policy that is attached to a custom model, including the JSON body of the policy\.

## Request Syntax<a name="API_DescribeResourcePolicy_RequestSyntax"></a>

```
{
   "ResourceArn": "string"
}
```

## Request Parameters<a name="API_DescribeResourcePolicy_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ResourceArn](#API_DescribeResourcePolicy_RequestSyntax) **   <a name="comprehend-DescribeResourcePolicy-request-ResourceArn"></a>
The Amazon Resource Name \(ARN\) of the policy to describe\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier|entity-recognizer)/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

## Response Syntax<a name="API_DescribeResourcePolicy_ResponseSyntax"></a>

```
{
   "CreationTime": number,
   "LastModifiedTime": number,
   "PolicyRevisionId": "string",
   "ResourcePolicy": "string"
}
```

## Response Elements<a name="API_DescribeResourcePolicy_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [CreationTime](#API_DescribeResourcePolicy_ResponseSyntax) **   <a name="comprehend-DescribeResourcePolicy-response-CreationTime"></a>
The time at which the policy was created\.  
Type: Timestamp

 ** [LastModifiedTime](#API_DescribeResourcePolicy_ResponseSyntax) **   <a name="comprehend-DescribeResourcePolicy-response-LastModifiedTime"></a>
The time at which the policy was last modified\.  
Type: Timestamp

 ** [PolicyRevisionId](#API_DescribeResourcePolicy_ResponseSyntax) **   <a name="comprehend-DescribeResourcePolicy-response-PolicyRevisionId"></a>
The revision ID of the policy\. Each time you modify a policy, Amazon Comprehend assigns a new revision ID, and it deletes the prior version of the policy\.  
Type: String  
Length Constraints: Maximum length of 64\.  
Pattern: `[0-9A-Fa-f]+` 

 ** [ResourcePolicy](#API_DescribeResourcePolicy_ResponseSyntax) **   <a name="comprehend-DescribeResourcePolicy-response-ResourcePolicy"></a>
The JSON body of the resource\-based policy\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 20000\.  
Pattern: `[\u0009\u000A\u000D\u0020-\u00FF]+` 

## Errors<a name="API_DescribeResourcePolicy_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** ResourceNotFoundException **   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeResourcePolicy_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeResourcePolicy) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeResourcePolicy) 