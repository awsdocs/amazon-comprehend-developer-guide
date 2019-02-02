# CreateDocumentClassifier<a name="API_CreateDocumentClassifier"></a>

Creates a new document classifier that you can use to categorize documents\. To create a classifier you provide a set of training documents that labeled with the categories that you want to use\. After the classifier is trained you can use it to categorize a set of labeled documents into the categories\. For more information, see [Custom Classification](how-document-classification.md)\.

## Request Syntax<a name="API_CreateDocumentClassifier_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-CreateDocumentClassifier-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-CreateDocumentClassifier-request-DataAccessRoleArn)": "string",
   "[DocumentClassifierName](#comprehend-CreateDocumentClassifier-request-DocumentClassifierName)": "string",
   "[InputDataConfig](#comprehend-CreateDocumentClassifier-request-InputDataConfig)": { 
      "[S3Uri](API_DocumentClassifierInputDataConfig.md#comprehend-Type-DocumentClassifierInputDataConfig-S3Uri)": "string"
   },
   "[LanguageCode](#comprehend-CreateDocumentClassifier-request-LanguageCode)": "string"
}
```

## Request Parameters<a name="API_CreateDocumentClassifier_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_CreateDocumentClassifier_RequestSyntax) **   <a name="comprehend-CreateDocumentClassifier-request-ClientRequestToken"></a>
A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_CreateDocumentClassifier_RequestSyntax) **   <a name="comprehend-CreateDocumentClassifier-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [DocumentClassifierName](#API_CreateDocumentClassifier_RequestSyntax) **   <a name="comprehend-CreateDocumentClassifier-request-DocumentClassifierName"></a>
The name of the document classifier\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** [InputDataConfig](#API_CreateDocumentClassifier_RequestSyntax) **   <a name="comprehend-CreateDocumentClassifier-request-InputDataConfig"></a>
Specifies the format and location of the input data for the job\.  
Type: [DocumentClassifierInputDataConfig](API_DocumentClassifierInputDataConfig.md) object  
Required: Yes

 ** [LanguageCode](#API_CreateDocumentClassifier_RequestSyntax) **   <a name="comprehend-CreateDocumentClassifier-request-LanguageCode"></a>
The language of the input documents\. You can specify English \("en"\) or Spanish \("es"\)\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: Yes

## Response Syntax<a name="API_CreateDocumentClassifier_ResponseSyntax"></a>

```
{
   "[DocumentClassifierArn](#comprehend-CreateDocumentClassifier-response-DocumentClassifierArn)": "string"
}
```

## Response Elements<a name="API_CreateDocumentClassifier_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [DocumentClassifierArn](#API_CreateDocumentClassifier_ResponseSyntax) **   <a name="comprehend-CreateDocumentClassifier-response-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*` 

## Errors<a name="API_CreateDocumentClassifier_Errors"></a>

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

 **TooManyRequestsException**   
The number of requests exceeds the limit\. Resubmit your request later\.  
HTTP Status Code: 400

 **UnsupportedLanguageException**   
Amazon Comprehend can't process the language of the input text\. For all custom entity recognition APIs \(such as `CreateEntityRecognizer`\), only English is accepted\. For most other APIs, Amazon Comprehend accepts only English or Spanish text\.   
HTTP Status Code: 400

## See Also<a name="API_CreateDocumentClassifier_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/CreateDocumentClassifier) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/CreateDocumentClassifier) 