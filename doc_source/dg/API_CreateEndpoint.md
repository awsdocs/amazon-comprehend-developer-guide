# CreateEndpoint<a name="API_CreateEndpoint"></a>

Creates a model\-specific endpoint for synchronous inference for a previously trained custom model 

## Request Syntax<a name="API_CreateEndpoint_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-CreateEndpoint-request-ClientRequestToken)": "string",
   "[DesiredInferenceUnits](#comprehend-CreateEndpoint-request-DesiredInferenceUnits)": number,
   "[EndpointName](#comprehend-CreateEndpoint-request-EndpointName)": "string",
   "[ModelArn](#comprehend-CreateEndpoint-request-ModelArn)": "string",
   "[Tags](#comprehend-CreateEndpoint-request-Tags)": [ 
      { 
         "[Key](API_Tag.md#comprehend-Type-Tag-Key)": "string",
         "[Value](API_Tag.md#comprehend-Type-Tag-Value)": "string"
      }
   ]
}
```

## Request Parameters<a name="API_CreateEndpoint_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_CreateEndpoint_RequestSyntax) **   <a name="comprehend-CreateEndpoint-request-ClientRequestToken"></a>
An idempotency token provided by the customer\. If this token matches a previous endpoint creation request, Amazon Comprehend will not return a `ResourceInUseException`\.   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DesiredInferenceUnits](#API_CreateEndpoint_RequestSyntax) **   <a name="comprehend-CreateEndpoint-request-DesiredInferenceUnits"></a>
 The desired number of inference units to be used by the model using this endpoint\. Each inference unit represents of a throughput of 100 characters per second\.  
Type: Integer  
Valid Range: Minimum value of 1\.  
Required: Yes

 ** [EndpointName](#API_CreateEndpoint_RequestSyntax) **   <a name="comprehend-CreateEndpoint-request-EndpointName"></a>
This is the descriptive suffix that becomes part of the `EndpointArn` used for all subsequent requests to this resource\.   
Type: String  
Length Constraints: Maximum length of 40\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: Yes

 ** [ModelArn](#API_CreateEndpoint_RequestSyntax) **   <a name="comprehend-CreateEndpoint-request-ModelArn"></a>
The Amazon Resource Number \(ARN\) of the model to which the endpoint will be attached\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** [Tags](#API_CreateEndpoint_RequestSyntax) **   <a name="comprehend-CreateEndpoint-request-Tags"></a>
Tags associated with the endpoint being created\. A tag is a key\-value pair that adds metadata to the endpoint\. For example, a tag with "Sales" as the key might be added to an endpoint to indicate its use by the sales department\.   
Type: Array of [Tag](API_Tag.md) objects  
Required: No

## Response Syntax<a name="API_CreateEndpoint_ResponseSyntax"></a>

```
{
   "[EndpointArn](#comprehend-CreateEndpoint-response-EndpointArn)": "string"
}
```

## Response Elements<a name="API_CreateEndpoint_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EndpointArn](#API_CreateEndpoint_ResponseSyntax) **   <a name="comprehend-CreateEndpoint-response-EndpointArn"></a>
The Amazon Resource Number \(ARN\) of the endpoint being created\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier-endpoint/[a-zA-Z0-9](-*[a-zA-Z0-9])*` 

## Errors<a name="API_CreateEndpoint_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **ResourceInUseException**   
The specified name is already in use\. Use a different name and try your request again\.  
HTTP Status Code: 400

 **ResourceLimitExceededException**   
The maximum number of recognizers per account has been exceeded\. Review the recognizers, perform cleanup, and then try your request again\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **ResourceUnavailableException**   
The specified resource is not available\. Check to see if the resource is in the `TRAINED` state and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 **TooManyTagsException**   
The request contains more tags than can be associated with a resource \(50 tags per resource\)\. The maximum number of tags includes both existing tags and those included in your current request\.   
HTTP Status Code: 400

## See Also<a name="API_CreateEndpoint_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/CreateEndpoint) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/CreateEndpoint) 