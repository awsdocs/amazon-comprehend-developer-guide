# ContainsPiiEntities<a name="API_ContainsPiiEntities"></a>

Analyzes input text for the presence of personally identifiable information \(PII\) and returns the labels of identified PII entity types such as name, address, bank account number, or phone number\.

## Request Syntax<a name="API_ContainsPiiEntities_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_ContainsPiiEntities_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_ContainsPiiEntities_RequestSyntax) **   <a name="comprehend-ContainsPiiEntities-request-LanguageCode"></a>
The language of the input documents\. Currently, English is the only valid language\.  
Type: String  
Valid Values:` en`   
Required: Yes

 ** [Text](#API_ContainsPiiEntities_RequestSyntax) **   <a name="comprehend-ContainsPiiEntities-request-Text"></a>
A UTF\-8 text string\. The maximum string size is 100 KB\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_ContainsPiiEntities_ResponseSyntax"></a>

```
{
   "Labels": [ 
      { 
         "Name": "string",
         "Score": number
      }
   ]
}
```

## Response Elements<a name="API_ContainsPiiEntities_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Labels](#API_ContainsPiiEntities_ResponseSyntax) **   <a name="comprehend-ContainsPiiEntities-response-Labels"></a>
The labels used in the document being analyzed\. Individual labels represent personally identifiable information \(PII\) entity types\.  
Type: Array of [EntityLabel](API_EntityLabel.md) objects

## Errors<a name="API_ContainsPiiEntities_Errors"></a>

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
Amazon Comprehend can't process the language of the input text\. For custom entity recognition APIs, only English, Spanish, French, Italian, German, or Portuguese are accepted\. For a list of supported languages, [Supported languages](https://docs.aws.amazon.com/comprehend/latest/dg/supported-languages.html) in the Comprehend Developer Guide\.   
HTTP Status Code: 400

## See Also<a name="API_ContainsPiiEntities_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/ContainsPiiEntities) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/ContainsPiiEntities) 