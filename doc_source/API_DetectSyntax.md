# DetectSyntax<a name="API_DetectSyntax"></a>

Inspects text for syntax and the part of speech of words in the document\. For more information, [Syntax analysis](how-syntax.md)\.

## Request Syntax<a name="API_DetectSyntax_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_DetectSyntax_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_DetectSyntax_RequestSyntax) **   <a name="comprehend-DetectSyntax-request-LanguageCode"></a>
The language code of the input documents\. You can specify any of the following languages supported by Amazon Comprehend: German \("de"\), English \("en"\), Spanish \("es"\), French \("fr"\), Italian \("it"\), or Portuguese \("pt"\)\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: Yes

 ** [Text](#API_DetectSyntax_RequestSyntax) **   <a name="comprehend-DetectSyntax-request-Text"></a>
A UTF\-8 string\. Each string must contain fewer that 5,000 bytes of UTF encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectSyntax_ResponseSyntax"></a>

```
{
   "SyntaxTokens": [ 
      { 
         "BeginOffset": number,
         "EndOffset": number,
         "PartOfSpeech": { 
            "Score": number,
            "Tag": "string"
         },
         "Text": "string",
         "TokenId": number
      }
   ]
}
```

## Response Elements<a name="API_DetectSyntax_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [SyntaxTokens](#API_DetectSyntax_ResponseSyntax) **   <a name="comprehend-DetectSyntax-response-SyntaxTokens"></a>
A collection of syntax tokens describing the text\. For each token, the response provides the text, the token type, where the text begins and ends, and the level of confidence that Amazon Comprehend has that the token is correct\. For a list of token types, see [Syntax analysis](how-syntax.md)\.  
Type: Array of [SyntaxToken](API_SyntaxToken.md) objects

## Errors<a name="API_DetectSyntax_Errors"></a>

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
Amazon Comprehend can't process the language of the input text\. For custom entity recognition APIs, only English, Spanish, French, Italian, German, or Portuguese are accepted\. For a list of supported languages, see [Languages supported in Amazon Comprehend](supported-languages.md)\.   
HTTP Status Code: 400

## See Also<a name="API_DetectSyntax_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DetectSyntax) 