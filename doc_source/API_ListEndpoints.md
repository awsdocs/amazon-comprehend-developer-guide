# ListEndpoints<a name="API_ListEndpoints"></a>

Gets a list of all existing endpoints that you've created\.

## Request Syntax<a name="API_ListEndpoints_RequestSyntax"></a>

```
{
   "Filter": { 
      "CreationTimeAfter": number,
      "CreationTimeBefore": number,
      "ModelArn": "string",
      "Status": "string"
   },
   "MaxResults": number,
   "NextToken": "string"
}
```

## Request Parameters<a name="API_ListEndpoints_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ Filter ](#API_ListEndpoints_RequestSyntax) **   <a name="comprehend-ListEndpoints-request-Filter"></a>
Filters the endpoints that are returned\. You can filter endpoints on their name, model, status, or the date and time that they were created\. You can only set one filter at a time\.   
Type: [ EndpointFilter ](API_EndpointFilter.md) object  
Required: No

 ** [ MaxResults ](#API_ListEndpoints_RequestSyntax) **   <a name="comprehend-ListEndpoints-request-MaxResults"></a>
The maximum number of results to return in each page\. The default is 100\.  
Type: Integer  
Valid Range: Minimum value of 1\. Maximum value of 500\.  
Required: No

 ** [ NextToken ](#API_ListEndpoints_RequestSyntax) **   <a name="comprehend-ListEndpoints-request-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## Response Syntax<a name="API_ListEndpoints_ResponseSyntax"></a>

```
{
   "EndpointPropertiesList": [ 
      { 
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
   ],
   "NextToken": "string"
}
```

## Response Elements<a name="API_ListEndpoints_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ EndpointPropertiesList ](#API_ListEndpoints_ResponseSyntax) **   <a name="comprehend-ListEndpoints-response-EndpointPropertiesList"></a>
Displays a list of endpoint properties being retrieved by the service in response to the request\.  
Type: Array of [ EndpointProperties ](API_EndpointProperties.md) objects

 ** [ NextToken ](#API_ListEndpoints_ResponseSyntax) **   <a name="comprehend-ListEndpoints-response-NextToken"></a>
Identifies the next page of results to return\.  
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_ListEndpoints_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** TooManyRequestsException **   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_ListEndpoints_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ListEndpoints) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ListEndpoints) 