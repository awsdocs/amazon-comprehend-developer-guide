# DeleteDocumentClassifier<a name="API_DeleteDocumentClassifier"></a>

Deletes a previously created document classifier

Only those classifiers that are in terminated states \(IN\_ERROR, TRAINED\) will be deleted\. If an active inference job is using the model, a `ResourceInUseException` will be returned\.

This is an asynchronous action that puts the classifier into a DELETING state, and it is then removed by a background job\. Once removed, the classifier disappears from your account and is no longer available for use\. 

## Request Syntax<a name="API_DeleteDocumentClassifier_RequestSyntax"></a>

```
{
   "[DocumentClassifierArn](#comprehend-DeleteDocumentClassifier-request-DocumentClassifierArn)": "string"
}
```

## Request Parameters<a name="API_DeleteDocumentClassifier_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [DocumentClassifierArn](#API_DeleteDocumentClassifier_RequestSyntax) **   <a name="comprehend-DeleteDocumentClassifier-request-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\.   
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Elements<a name="API_DeleteDocumentClassifier_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response with an empty HTTP body\.

## Errors<a name="API_DeleteDocumentClassifier_Errors"></a>

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

 **ResourceNotFoundException**   
The specified resource ARN was not found\. Check the ARN and try your request again\.  
HTTP Status Code: 400

 **ResourceUnavailableException**   
The specified resource is not available\. Check to see if the resource is in the `TRAINED` state and try your request again\.  
HTTP Status Code: 400

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

## See Also<a name="API_DeleteDocumentClassifier_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DeleteDocumentClassifier) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DeleteDocumentClassifier) 