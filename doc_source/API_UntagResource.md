# UntagResource<a name="API_UntagResource"></a>

Removes a specific tag associated with an Amazon Comprehend resource\. 

## Request Syntax<a name="API_UntagResource_RequestSyntax"></a>

```
{
   "[ResourceArn](#comprehend-UntagResource-request-ResourceArn)": "string",
   "[TagKeys](#comprehend-UntagResource-request-TagKeys)": [ "string" ]
}
```

## Request Parameters<a name="API_UntagResource_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ResourceArn](#API_UntagResource_RequestSyntax) **   <a name="comprehend-UntagResource-request-ResourceArn"></a>
 The Amazon Resource Name \(ARN\) of the given Amazon Comprehend resource from which you want to remove the tags\.   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** [TagKeys](#API_UntagResource_RequestSyntax) **   <a name="comprehend-UntagResource-request-TagKeys"></a>
The initial part of a key\-value pair that forms a tag being removed from a given resource\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\. Keys must be unique and cannot be duplicated for a particular resource\.   
Type: Array of strings  
Length Constraints: Minimum length of 1\. Maximum length of 128\.  
Required: Yes

## Response Elements<a name="API_UntagResource_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response with an empty HTTP body\.

## Errors<a name="API_UntagResource_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **ConcurrentModificationException**   
Concurrent modification of the tags associated with an Amazon Comprehend resource is not supported\.   
HTTP Status Code: 400

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **TooManyTagKeysException**   
The request contains more tag keys than can be associated with a resource \(50 tag keys per resource\)\.  
HTTP Status Code: 400

## See Also<a name="API_UntagResource_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/UntagResource) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/UntagResource) 