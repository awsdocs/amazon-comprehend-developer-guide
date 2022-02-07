# DetectPiiEntities<a name="API_DetectPiiEntities"></a>

Inspects the input text for entities that contain personally identifiable information \(PII\) and returns information about them\.

## Request Syntax<a name="API_DetectPiiEntities_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_DetectPiiEntities_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_DetectPiiEntities_RequestSyntax) **   <a name="comprehend-DetectPiiEntities-request-LanguageCode"></a>
The language of the input documents\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [Text](#API_DetectPiiEntities_RequestSyntax) **   <a name="comprehend-DetectPiiEntities-request-Text"></a>
A UTF\-8 text string\. Each string must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectPiiEntities_ResponseSyntax"></a>

```
{
   "Entities": [ 
      { 
         "BeginOffset": number,
         "EndOffset": number,
         "Score": number,
         "Type": "string"
      }
   ]
}
```

## Response Elements<a name="API_DetectPiiEntities_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Entities](#API_DetectPiiEntities_ResponseSyntax) **   <a name="comprehend-DetectPiiEntities-response-Entities"></a>
A collection of PII entities identified in the input text\. For each entity, the response provides the entity type, where the entity text begins and ends, and the level of confidence that Amazon Comprehend has in the detection\.  
Type: Array of [PiiEntity](API_PiiEntity.md) objects

## Errors<a name="API_DetectPiiEntities_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** TextSizeLimitExceededException **   
The size of the input text exceeds the limit\. Use a smaller document\.  
HTTP Status Code: 400

 ** UnsupportedLanguageException **   
Amazon Comprehend can't process the language of the input text\. For custom entity recognition APIs, only English, Spanish, French, Italian, German, or Portuguese are accepted\. For a list of supported languages, see [Languages Supported in Amazon Comprehend](supported-languages.md)\.   
HTTP Status Code: 400

## See Also<a name="API_DetectPiiEntities_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectPiiEntities) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DetectPiiEntities) 