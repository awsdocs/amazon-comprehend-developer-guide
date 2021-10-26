# StopTrainingDocumentClassifier<a name="API_StopTrainingDocumentClassifier"></a>

Stops a document classifier training job while in progress\.

If the training job state is `TRAINING`, the job is marked for termination and put into the `STOP_REQUESTED` state\. If the training job completes before it can be stopped, it is put into the `TRAINED`; otherwise the training job is stopped and put into the `STOPPED` state and the service sends back an HTTP 200 response with an empty HTTP body\. 

## Request Syntax<a name="API_StopTrainingDocumentClassifier_RequestSyntax"></a>

```
{
   "DocumentClassifierArn": "string"
}
```

## Request Parameters<a name="API_StopTrainingDocumentClassifier_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ DocumentClassifierArn ](#API_StopTrainingDocumentClassifier_RequestSyntax) **   <a name="comprehend-StopTrainingDocumentClassifier-request-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier currently being trained\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*(/version/[a-zA-Z0-9](-*[a-zA-Z0-9])*)?`   
Required: Yes

## Response Elements<a name="API_StopTrainingDocumentClassifier_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response with an empty HTTP body\.

## Errors<a name="API_StopTrainingDocumentClassifier_Errors"></a>

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

## See Also<a name="API_StopTrainingDocumentClassifier_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StopTrainingDocumentClassifier) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/StopTrainingDocumentClassifier) 