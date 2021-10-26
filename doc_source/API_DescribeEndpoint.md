# DescribeEndpoint<a name="API_DescribeEndpoint"></a>

Gets the properties associated with a specific endpoint\. Use this operation to get the status of an endpoint\.

## Request Syntax<a name="API_DescribeEndpoint_RequestSyntax"></a>

```
{
   "EndpointArn": "string"
}
```

## Request Parameters<a name="API_DescribeEndpoint_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ EndpointArn ](#API_DescribeEndpoint_RequestSyntax) **   <a name="comprehend-DescribeEndpoint-request-EndpointArn"></a>
The Amazon Resource Number \(ARN\) of the endpoint being described\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:(document-classifier-endpoint|entity-recognizer-endpoint)/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Syntax<a name="API_DescribeEndpoint_ResponseSyntax"></a>

```
{
   "EndpointProperties": { 
      "CreationTime": number,
      "CurrentInferenceUnits": number,
      "DataAccessRoleArn": "string",
      "DesiredDataAccessRoleArn": "string",
      "DesiredInferenceUnits": number,
      "DesiredModelArn": "string",
      "EndpointArn": "string",
      "LastModifiedTime": number,
      "Message": "string",
      "ModelArn": "string",
      "Status": "string"
   }
}
```

## Response Elements<a name="API_DescribeEndpoint_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ EndpointProperties ](#API_DescribeEndpoint_ResponseSyntax) **   <a name="comprehend-DescribeEndpoint-response-EndpointProperties"></a>
Describes information associated with the specific endpoint\.  
Type: [ EndpointProperties ](API_EndpointProperties.md) object

## Errors<a name="API_DescribeEndpoint_Errors"></a>

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

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DescribeEndpoint_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DescribeEndpoint) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DescribeEndpoint) 