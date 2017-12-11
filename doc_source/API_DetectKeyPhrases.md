# DetectKeyPhrases<a name="API_DetectKeyPhrases"></a>

Detects the key noun phrases found in the text\. 

## Request Syntax<a name="API_DetectKeyPhrases_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_DetectKeyPhrases_RequestParameters"></a>

For information about the parameters that are common to all actions, see Common Parameters\.

The request accepts the following data in JSON format\.

 ** LanguageCode **   
The RFC 5646 language code for the input text\. If you specify the code for a language that Amazon Comprehend does not support, it returns and `UnsupportedLanguageException`\. For more information about RFC 5646, see [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646) on the *IETF Tools* web site\.  
Type: String  
Valid Values:` en | es`   
Required: Yes

 ** Text **   
A UTF\-8 text string\. Each string must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectKeyPhrases_ResponseSyntax"></a>

```
{
   "KeyPhrases": [ 
      { 
         "BeginOffset": number,
         "EndOffset": number,
         "Score": number,
         "Text": "string"
      }
   ]
}
```

## Response Elements<a name="API_DetectKeyPhrases_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** KeyPhrases **   
A collection of key phrases that Amazon Comprehend identified in the input text\. For each key phrase, the response provides the text of the key phrase, where the key phrase begins and ends, and the level of confidence that Amazon Comprehend has in the accuracy of the detection\.   
Type: Array of [KeyPhrase](API_KeyPhrase.md) objects

## Errors<a name="API_DetectKeyPhrases_Errors"></a>

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
Amazon Comprehend can't process the language of the input text\. For all APIs except `DetectDominantLanguage`, Amazon Comprehend accepts only English or Spanish text\. For the `DetectDominantLanguage` API, Amazon Comprehend detects 100 languages\. For a list of languages, see [Detecting the Primary Language ](how-languages.md)   
HTTP Status Code: 400

## Example<a name="API_DetectKeyPhrases_Examples"></a>

### Detect phrases<a name="API_DetectKeyPhrases_Example_1"></a>

If the input text is "Bob lives in Seattle\. He is a software engineer at Amazon\.", the API returns the following:

#### <a name="w3ab1c23b5c29c15b3b5"></a>

```
          {
    "KeyPhrases": [
        {
            "Text": "Bob",
            "Score": 1.0,
            "BeginOffset": 0,
            "EndOffset": 3
        },
        {
            "Text": "Seattle",
            "Score": 1.0,
            "BeginOffset": 13,
            "EndOffset": 20
        },
        {
            "Text": "an engineer",
            "Score": 1.0,
            "BeginOffset": 28,
            "EndOffset": 39
        },
        {
            "Text": "Amazon",
            "Score": 1.0,
            "BeginOffset": 43,
            "EndOffset": 49
        }
    ]
}}
```

## See Also<a name="API_DetectKeyPhrases_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectKeyPhrases) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DetectKeyPhrases) 