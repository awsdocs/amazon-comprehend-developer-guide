# CreateEntityRecognizer<a name="API_CreateEntityRecognizer"></a>

Creates an entity recognizer using submitted files\. After your `CreateEntityRecognizer` request is submitted, you can check job status using the [DescribeEntityRecognizer](API_DescribeEntityRecognizer.md) API\. 

## Request Syntax<a name="API_CreateEntityRecognizer_RequestSyntax"></a>

```
{
   "[ClientRequestToken](#comprehend-CreateEntityRecognizer-request-ClientRequestToken)": "string",
   "[DataAccessRoleArn](#comprehend-CreateEntityRecognizer-request-DataAccessRoleArn)": "string",
   "[InputDataConfig](#comprehend-CreateEntityRecognizer-request-InputDataConfig)": { 
      "[Annotations](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-Annotations)": { 
         "[S3Uri](API_EntityRecognizerAnnotations.md#comprehend-Type-EntityRecognizerAnnotations-S3Uri)": "string"
      },
      "[Documents](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-Documents)": { 
         "[S3Uri](API_EntityRecognizerDocuments.md#comprehend-Type-EntityRecognizerDocuments-S3Uri)": "string"
      },
      "[EntityList](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-EntityList)": { 
         "[S3Uri](API_EntityRecognizerEntityList.md#comprehend-Type-EntityRecognizerEntityList-S3Uri)": "string"
      },
      "[EntityTypes](API_EntityRecognizerInputDataConfig.md#comprehend-Type-EntityRecognizerInputDataConfig-EntityTypes)": [ 
         { 
            "[Type](API_EntityTypesListItem.md#comprehend-Type-EntityTypesListItem-Type)": "string"
         }
      ]
   },
   "[LanguageCode](#comprehend-CreateEntityRecognizer-request-LanguageCode)": "string",
   "[RecognizerName](#comprehend-CreateEntityRecognizer-request-RecognizerName)": "string"
}
```

## Request Parameters<a name="API_CreateEntityRecognizer_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [ClientRequestToken](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-ClientRequestToken"></a>
 A unique identifier for the request\. If you don't set the client request token, Amazon Comprehend generates one\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 64\.  
Pattern: `^[a-zA-Z0-9-]+$`   
Required: No

 ** [DataAccessRoleArn](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: Yes

 ** [InputDataConfig](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-InputDataConfig"></a>
Specifies the format and location of the input data\. The S3 bucket containing the input data must be located in the same region as the entity recognizer being created\.   
Type: [EntityRecognizerInputDataConfig](API_EntityRecognizerInputDataConfig.md) object  
Required: Yes

 ** [LanguageCode](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-LanguageCode"></a>
 The language of the input documents\. All documents must be in the same language\. Only English \("en"\) is currently supported\.   
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: Yes

 ** [RecognizerName](#API_CreateEntityRecognizer_RequestSyntax) **   <a name="comprehend-CreateEntityRecognizer-request-RecognizerName"></a>
The name given to the newly created recognizer\. Recognizer names can be a maximum of 256 characters\. Alphanumeric characters, hyphens \(\-\) and underscores \(\_\) are allowed\. The name must be unique in the account/region\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

## Response Syntax<a name="API_CreateEntityRecognizer_ResponseSyntax"></a>

```
{
   "[EntityRecognizerArn](#comprehend-CreateEntityRecognizer-response-EntityRecognizerArn)": "string"
}
```

## Response Elements<a name="API_CreateEntityRecognizer_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [EntityRecognizerArn](#API_CreateEntityRecognizer_ResponseSyntax) **   <a name="comprehend-CreateEntityRecognizer-response-EntityRecognizerArn"></a>
The Amazon Resource Name \(ARN\) that identifies the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer/[a-zA-Z0-9](-*[a-zA-Z0-9])*` 

## Errors<a name="API_CreateEntityRecognizer_Errors"></a>

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

## See Also<a name="API_CreateEntityRecognizer_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/CreateEntityRecognizer) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/CreateEntityRecognizer) 