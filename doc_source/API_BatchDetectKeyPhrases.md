# BatchDetectKeyPhrases<a name="API_BatchDetectKeyPhrases"></a>

Detects the key noun phrases found in a batch of documents\.

## Request Syntax<a name="API_BatchDetectKeyPhrases_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "TextList": [ "string" ]
}
```

## Request Parameters<a name="API_BatchDetectKeyPhrases_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_BatchDetectKeyPhrases_RequestSyntax) **   <a name="comprehend-BatchDetectKeyPhrases-request-LanguageCode"></a>
The language of the input documents\. You can specify any of the primary languages supported by Amazon Comprehend\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: Yes

 ** [TextList](#API_BatchDetectKeyPhrases_RequestSyntax) **   <a name="comprehend-BatchDetectKeyPhrases-request-TextList"></a>
A list containing the UTF\-8 encoded text of the input documents\. The list can contain a maximum of 25 documents\. The maximum size of each document is 5 KB\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_BatchDetectKeyPhrases_ResponseSyntax"></a>

```
{
   "ErrorList": [ 
      { 
         "ErrorCode": "string",
         "ErrorMessage": "string",
         "Index": number
      }
   ],
   "ResultList": [ 
      { 
         "Index": number,
         "KeyPhrases": [ 
            { 
               "BeginOffset": number,
               "EndOffset": number,
               "Score": number,
               "Text": "string"
            }
         ]
      }
   ]
}
```

## Response Elements<a name="API_BatchDetectKeyPhrases_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ErrorList](#API_BatchDetectKeyPhrases_ResponseSyntax) **   <a name="comprehend-BatchDetectKeyPhrases-response-ErrorList"></a>
A list containing one [BatchItemError](API_BatchItemError.md) object for each document that contained an error\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If there are no errors in the batch, the `ErrorList` is empty\.  
Type: Array of [BatchItemError](API_BatchItemError.md) objects

 ** [ResultList](#API_BatchDetectKeyPhrases_ResponseSyntax) **   <a name="comprehend-BatchDetectKeyPhrases-response-ResultList"></a>
A list of [BatchDetectKeyPhrasesItemResult](API_BatchDetectKeyPhrasesItemResult.md) objects containing the results of the operation\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If all of the documents contain an error, the `ResultList` is empty\.  
Type: Array of [BatchDetectKeyPhrasesItemResult](API_BatchDetectKeyPhrasesItemResult.md) objects

## Errors<a name="API_BatchDetectKeyPhrases_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** BatchSizeLimitExceededException **   
The number of documents in the request exceeds the limit of 25\. Try your request again with fewer documents\.  
HTTP Status Code: 400

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

## See Also<a name="API_BatchDetectKeyPhrases_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/BatchDetectKeyPhrases) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/BatchDetectKeyPhrases) 