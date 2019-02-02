# StopTrainingEntityRecognizer<a name="API_StopTrainingEntityRecognizer"></a>

Stops an entity recognizer training job while in progress\.

If the training job state is `TRAINING`, the job is marked for termination and put into the `STOP_REQUESTED` state\. If the training job completes before it can be stopped, it is put into the `TRAINED`; otherwise the training job is stopped and putted into the `STOPPED` state and the service sends back an HTTP 200 response with an empty HTTP body\.

## Request Syntax<a name="API_StopTrainingEntityRecognizer_RequestSyntax"></a>

```
{
   "[EntityRecognizerArn](#comprehend-StopTrainingEntityRecognizer-request-EntityRecognizerArn)": "string"
}
```

## Request Parameters<a name="API_StopTrainingEntityRecognizer_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [EntityRecognizerArn](#API_StopTrainingEntityRecognizer_RequestSyntax) **   <a name="comprehend-StopTrainingEntityRecognizer-request-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer currently being trained\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Elements<a name="API_StopTrainingEntityRecognizer_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response with an empty HTTP body\.

## Errors<a name="API_StopTrainingEntityRecognizer_Errors"></a>

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

## See Also<a name="API_StopTrainingEntityRecognizer_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/StopTrainingEntityRecognizer) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/StopTrainingEntityRecognizer) 