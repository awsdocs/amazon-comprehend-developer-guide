# DetectSentiment<a name="API_DetectSentiment"></a>

Inspects text and returns an inference of the prevailing sentiment \(`POSITIVE`, `NEUTRAL`, `MIXED`, or `NEGATIVE`\)\. 

## Request Syntax<a name="API_DetectSentiment_RequestSyntax"></a>

```
{
   "[LanguageCode](#comprehend-DetectSentiment-request-LanguageCode)": "string",
   "[Text](#comprehend-DetectSentiment-request-Text)": "string"
}
```

## Request Parameters<a name="API_DetectSentiment_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_DetectSentiment_RequestSyntax) **   <a name="comprehend-DetectSentiment-request-LanguageCode"></a>
The language of the input documents\. You can specify English \("en"\) or Spanish \("es"\)\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es`   
Required: Yes

 ** [Text](#API_DetectSentiment_RequestSyntax) **   <a name="comprehend-DetectSentiment-request-Text"></a>
A UTF\-8 text string\. Each string must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectSentiment_ResponseSyntax"></a>

```
{
   "[Sentiment](#comprehend-DetectSentiment-response-Sentiment)": "string",
   "[SentimentScore](#comprehend-DetectSentiment-response-SentimentScore)": { 
      "[Mixed](API_SentimentScore.md#comprehend-Type-SentimentScore-Mixed)": number,
      "[Negative](API_SentimentScore.md#comprehend-Type-SentimentScore-Negative)": number,
      "[Neutral](API_SentimentScore.md#comprehend-Type-SentimentScore-Neutral)": number,
      "[Positive](API_SentimentScore.md#comprehend-Type-SentimentScore-Positive)": number
   }
}
```

## Response Elements<a name="API_DetectSentiment_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Sentiment](#API_DetectSentiment_ResponseSyntax) **   <a name="comprehend-DetectSentiment-response-Sentiment"></a>
The inferred sentiment that Amazon Comprehend has the highest level of confidence in\.  
Type: String  
Valid Values:` POSITIVE | NEGATIVE | NEUTRAL | MIXED` 

 ** [SentimentScore](#API_DetectSentiment_ResponseSyntax) **   <a name="comprehend-DetectSentiment-response-SentimentScore"></a>
An object that lists the sentiments, and their corresponding confidence levels\.  
Type: [SentimentScore](API_SentimentScore.md) object

## Errors<a name="API_DetectSentiment_Errors"></a>

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

## Example<a name="API_DetectSentiment_Examples"></a>

### Detect sentiment<a name="API_DetectSentiment_Example_1"></a>

If the input text is "Today is my birthday, I am so happy\.", the operation returns the following response:

#### <a name="w3ab1c23b5c32c15b3b5"></a>

```
{
    "SentimentScore": {
        "Mixed": 0.0033542951568961143,
        "Positive": 0.9869875907897949,
        "Neutral": 0.008563132025301456,
        "Negative": 0.0010949420975521207
    },
    "Sentiment": "POSITIVE",
 }   
}
```

## See Also<a name="API_DetectSentiment_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectSentiment) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DetectSentiment) 