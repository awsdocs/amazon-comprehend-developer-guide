# DescribeEndpoint<a name="API_DescribeEndpoint"></a>

Gets the properties associated with a specific endpoint\. Use this operation to get the status of an endpoint\.

## Request Syntax<a name="API_DescribeEndpoint_RequestSyntax"></a>

```
{
   "[EndpointArn](#comprehend-DescribeEndpoint-request-EndpointArn)": "string"
}
```

## Request Parameters<a name="API_DescribeEndpoint_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [EndpointArn](#API_DescribeEndpoint_RequestSyntax) **   <a name="comprehend-DescribeEndpoint-request-EndpointArn"></a>
The Amazon Resource Number \(ARN\) of the endpoint being described\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier-endpoint/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Syntax<a name="API_DescribeEndpoint_ResponseSyntax"></a>

```
{
   "[EndpointProperties](#comprehend-DescribeEndpoint-response-EndpointProperties)": { 
      "[CreationTime](API_EndpointProperties.md#comprehend-Type-EndpointProperties-CreationTime)": number,
      "[CurrentInferenceUnits](API_EndpointProperties.md#comprehend-Type-EndpointProperties-CurrentInferenceUnits)": number,
      "[DesiredInferenceUnits](API_EndpointProperties.md#comprehend-Type-EndpointProperties-DesiredInferenceUnits)": number,
      "[EndpointArn](API_EndpointProperties.md#comprehend-Type-EndpointProperties-EndpointArn)": "string",
      "[LastModifiedTime](API_EndpointProperties.md#comprehend-Type-EndpointProperties-LastModifiedTime)": number,
      "[Message](API_EndpointProperties.md#comprehend-Type-EndpointProperties-Message)": "string",
      "[ModelArn](API_EndpointProperties.md#comprehend-Type-EndpointProperties-ModelArn)": "string",
      "[Status](API_EndpointProperties.md#comprehend-Type-EndpointProperties-Status)": "string"
   }
}
```

## Response Elements<a name="API_DescribeEndpoint_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EndpointProperties](#API_DescribeEndpoint_ResponseSyntax) **   <a name="comprehend-DescribeEndpoint-response-EndpointProperties"></a>
Describes information associated with the specific endpoint\.  
Type: [EndpointProperties](API_EndpointProperties.md) object

## Errors<a name="API_DescribeEndpoint_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeEndpoint_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeEndpoint) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeEndpoint) 