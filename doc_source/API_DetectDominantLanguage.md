# DetectDominantLanguage<a name="API_DetectDominantLanguage"></a>

Determines the dominant language of the input text\. For a list of languages that Amazon Comprehend can detect, see [Amazon Comprehend Supported Languages](https://docs.aws.amazon.com/comprehend/latest/dg/how-languages.html)\. 

## Request Syntax<a name="API_DetectDominantLanguage_RequestSyntax"></a>

```
{
   "[Text](#comprehend-DetectDominantLanguage-request-Text)": "string"
}
```

## Request Parameters<a name="API_DetectDominantLanguage_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Text](#API_DetectDominantLanguage_RequestSyntax) **   <a name="comprehend-DetectDominantLanguage-request-Text"></a>
A UTF\-8 text string\. Each string should contain at least 20 characters and must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectDominantLanguage_ResponseSyntax"></a>

```
{
   "[Languages](#comprehend-DetectDominantLanguage-response-Languages)": [ 
      { 
         "[LanguageCode](API_DominantLanguage.md#comprehend-Type-DominantLanguage-LanguageCode)": "string",
         "[Score](API_DominantLanguage.md#comprehend-Type-DominantLanguage-Score)": number
      }
   ]
}
```

## Response Elements<a name="API_DetectDominantLanguage_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Languages](#API_DetectDominantLanguage_ResponseSyntax) **   <a name="comprehend-DetectDominantLanguage-response-Languages"></a>
The languages that Amazon Comprehend detected in the input text\. For each language, the response returns the RFC 5646 language code and the level of confidence that Amazon Comprehend has in the accuracy of its inference\. For more information about RFC 5646, see [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646) on the *IETF Tools* web site\.  
Type: Array of [DominantLanguage](API_DominantLanguage.md) objects

## Errors<a name="API_DetectDominantLanguage_Errors"></a>

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

## Example<a name="API_DetectDominantLanguage_Examples"></a>

### Detect dominant language<a name="API_DetectDominantLanguage_Example_1"></a>

If the input text is "Bob lives in Seattle\. He is a software engineer at Amazon\.", the operation returns the following:

#### <a name="w3ab1c21b5c38c15b3b5"></a>

```
{
    "Languages": [
        {
            "LanguageCode": "en",
            "Score": 0.9774383902549744
        },
        {
            "LanguageCode": "de",
            "Score": 0.010717987082898617
        }
    ]
}
```

## See Also<a name="API_DetectDominantLanguage_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectDominantLanguage) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DetectDominantLanguage) 