# ClassifyDocument<a name="API_ClassifyDocument"></a>

Creates a new document classification request to analyze a single document in real\-time, using a previously created and trained custom model and an endpoint\.

## Request Syntax<a name="API_ClassifyDocument_RequestSyntax"></a>

```
{
   "EndpointArn": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_ClassifyDocument_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [EndpointArn](#API_ClassifyDocument_RequestSyntax) **   <a name="comprehend-ClassifyDocument-request-EndpointArn"></a>
The Amazon Resource Number \(ARN\) of the endpoint\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier-endpoint/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** [Text](#API_ClassifyDocument_RequestSyntax) **   <a name="comprehend-ClassifyDocument-request-Text"></a>
The document text to be analyzed\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_ClassifyDocument_ResponseSyntax"></a>

```
{
   "Classes": [ 
      { 
         "Name": "string",
         "Score": number
      }
   ],
   "Labels": [ 
      { 
         "Name": "string",
         "Score": number
      }
   ]
}
```

## Response Elements<a name="API_ClassifyDocument_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Classes](#API_ClassifyDocument_ResponseSyntax) **   <a name="comprehend-ClassifyDocument-response-Classes"></a>
The classes used by the document being analyzed\. These are used for multi\-class trained models\. Individual classes are mutually exclusive and each document is expected to have only a single class assigned to it\. For example, an animal can be a dog or a cat, but not both at the same time\.   
Type: Array of [DocumentClass](API_DocumentClass.md) objects

 ** [Labels](#API_ClassifyDocument_ResponseSyntax) **   <a name="comprehend-ClassifyDocument-response-Labels"></a>
The labels used the document being analyzed\. These are used for multi\-label trained models\. Individual labels represent different categories that are related in some manner and are not mutually exclusive\. For example, a movie can be just an action movie, or it can be an action movie, a science fiction movie, and a comedy, all at the same time\.   
Type: Array of [DocumentLabel](API_DocumentLabel.md) objects

## Errors<a name="API_ClassifyDocument_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** ResourceUnavailableException **   
The specified resource is not available\. Check the resource and try your request again\.  
HTTP Status Code: 400

 ** TextSizeLimitExceededException **   
The size of the input text exceeds the limit\. Use a smaller document\.  
HTTP Status Code: 400

## See Also<a name="API_ClassifyDocument_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ClassifyDocument) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ClassifyDocument) 