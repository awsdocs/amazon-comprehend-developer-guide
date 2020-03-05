# DetectSyntax<a name="API_DetectSyntax"></a>

Inspects text for syntax and the part of speech of words in the document\. For more information, [Analyze Syntax](how-syntax.md)\.

## Request Syntax<a name="API_DetectSyntax_RequestSyntax"></a>

```
{
   "[LanguageCode](#comprehend-DetectSyntax-request-LanguageCode)": "string",
   "[Text](#comprehend-DetectSyntax-request-Text)": "string"
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
   "[SyntaxTokens](#comprehend-DetectSyntax-response-SyntaxTokens)": [ 
      { 
         "[BeginOffset](API_SyntaxToken.md#comprehend-Type-SyntaxToken-BeginOffset)": number,
         "[EndOffset](API_SyntaxToken.md#comprehend-Type-SyntaxToken-EndOffset)": number,
         "[PartOfSpeech](API_SyntaxToken.md#comprehend-Type-SyntaxToken-PartOfSpeech)": { 
            "[Score](API_PartOfSpeechTag.md#comprehend-Type-PartOfSpeechTag-Score)": number,
            "[Tag](API_PartOfSpeechTag.md#comprehend-Type-PartOfSpeechTag-Tag)": "string"
         },
         "[Text](API_SyntaxToken.md#comprehend-Type-SyntaxToken-Text)": "string",
         "[TokenId](API_SyntaxToken.md#comprehend-Type-SyntaxToken-TokenId)": number
      }
   ]
}
```

## Response Elements<a name="API_DetectSyntax_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [SyntaxTokens](#API_DetectSyntax_ResponseSyntax) **   <a name="comprehend-DetectSyntax-response-SyntaxTokens"></a>
A collection of syntax tokens describing the text\. For each token, the response provides the text, the token type, where the text begins and ends, and the level of confidence that Amazon Comprehend has that the token is correct\. For a list of token types, see [Analyze Syntax](how-syntax.md)\.  
Type: Array of [SyntaxToken](API_SyntaxToken.md) objects

## Errors<a name="API_DetectSyntax_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400

 **TextSizeLimitExceededException**   
The size of the input text exceeds the limit\. Use a smaller document\.  
HTTP Status Code: 400

 **UnsupportedLanguageException**   
Amazon Comprehend can't process the language of the input text\. For all custom entity recognition APIs \(such as `CreateEntityRecognizer`\), only English is accepted\. For most other APIs, such as those for Custom Classification, Amazon Comprehend accepts text in all supported languages\. For a list of supported languages, see [Languages Supported in Amazon Comprehend](supported-languages.md)\.   
HTTP Status Code: 400

## See Also<a name="API_DetectSyntax_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectSyntax) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DetectSyntax) 