# ListTagsForResource<a name="API_ListTagsForResource"></a>

Lists all tags associated with a given Amazon Comprehend resource\. 

## Request Syntax<a name="API_ListTagsForResource_RequestSyntax"></a>

```
{
   "ResourceArn": "string"
}
```

## Request Parameters<a name="API_ListTagsForResource_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ResourceArn](#API_ListTagsForResource_RequestSyntax) **   <a name="comprehend-ListTagsForResource-request-ResourceArn"></a>
The Amazon Resource Name \(ARN\) of the given Amazon Comprehend resource you are querying\.   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

## Response Syntax<a name="API_ListTagsForResource_ResponseSyntax"></a>

```
{
   "ResourceArn": "string",
   "Tags": [ 
      { 
         "Key": "string",
         "Value": "string"
      }
   ]
}
```

## Response Elements<a name="API_ListTagsForResource_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ResourceArn](#API_ListTagsForResource_ResponseSyntax) **   <a name="comprehend-ListTagsForResource-response-ResourceArn"></a>
The Amazon Resource Name \(ARN\) of the given Amazon Comprehend resource you are querying\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:[a-zA-Z0-9-]{1,64}/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?` 

 ** [Tags](#API_ListTagsForResource_ResponseSyntax) **   <a name="comprehend-ListTagsForResource-response-Tags"></a>
Tags associated with the Amazon Comprehend resource being queried\. A tag is a key\-value pair that adds as a metadata to a resource used by Amazon Comprehend\. For example, a tag with "Sales" as the key might be added to a resource to indicate its use by the sales department\.   
Type: Array of [Tag](API_Tag.md) objects

## Errors<a name="API_ListTagsForResource_Errors"></a>

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

## See Also<a name="API_ListTagsForResource_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListTagsForResource) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListTagsForResource) 