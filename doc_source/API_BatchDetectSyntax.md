# BatchDetectSyntax<a name="API_BatchDetectSyntax"></a>

Inspects the text of a batch of documents for the syntax and part of speech of the words in the document and returns information about them\. For more information, see [Analyze Syntax](how-syntax.md)\.

## Request Syntax<a name="API_BatchDetectSyntax_RequestSyntax"></a>

```
{
   "[LanguageCode](#comprehend-BatchDetectSyntax-request-LanguageCode)": "string",
   "[TextList](#comprehend-BatchDetectSyntax-request-TextList)": [ "string" ]
}
```

## Request Parameters<a name="API_BatchDetectSyntax_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_BatchDetectSyntax_RequestSyntax) **   <a name="comprehend-BatchDetectSyntax-request-LanguageCode"></a>
The language of the input documents\. You can specify English \("en"\) or Spanish \("es"\)\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: Yes

 ** [TextList](#API_BatchDetectSyntax_RequestSyntax) **   <a name="comprehend-BatchDetectSyntax-request-TextList"></a>
A list containing the text of the input documents\. The list can contain a maximum of 25 documents\. Each document must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_BatchDetectSyntax_ResponseSyntax"></a>

```
{
   "[ErrorList](#comprehend-BatchDetectSyntax-response-ErrorList)": [ 
      { 
         "[ErrorCode](API_BatchItemError.md#comprehend-Type-BatchItemError-ErrorCode)": "string",
         "[ErrorMessage](API_BatchItemError.md#comprehend-Type-BatchItemError-ErrorMessage)": "string",
         "[Index](API_BatchItemError.md#comprehend-Type-BatchItemError-Index)": number
      }
   ],
   "[ResultList](#comprehend-BatchDetectSyntax-response-ResultList)": [ 
      { 
         "[Index](API_BatchDetectSyntaxItemResult.md#comprehend-Type-BatchDetectSyntaxItemResult-Index)": number,
         "[SyntaxTokens](API_BatchDetectSyntaxItemResult.md#comprehend-Type-BatchDetectSyntaxItemResult-SyntaxTokens)": [ 
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
   ]
}
```

## Response Elements<a name="API_BatchDetectSyntax_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [ErrorList](#API_BatchDetectSyntax_ResponseSyntax) **   <a name="comprehend-BatchDetectSyntax-response-ErrorList"></a>
A list containing one [BatchItemError](API_BatchItemError.md) object for each document that contained an error\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If there are no errors in the batch, the `ErrorList` is empty\.  
Type: Array of [BatchItemError](API_BatchItemError.md) objects

 ** [ResultList](#API_BatchDetectSyntax_ResponseSyntax) **   <a name="comprehend-BatchDetectSyntax-response-ResultList"></a>
A list of [BatchDetectSyntaxItemResult](API_BatchDetectSyntaxItemResult.md) objects containing the results of the operation\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If all of the documents contain an error, the `ResultList` is empty\.  
Type: Array of [BatchDetectSyntaxItemResult](API_BatchDetectSyntaxItemResult.md) objects

## Errors<a name="API_BatchDetectSyntax_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **BatchSizeLimitExceededException**   
The number of documents in the request exceeds the limit of 25\. Try your request again with fewer documents\.  
HTTP Status Code: 400

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
Amazon Comprehend can't process the language of the input text\. For all custom entity recognition APIs \(such as `CreateEntityRecognizer`\), only English is accepted\. For most other APIs, Amazon Comprehend accepts only English or Spanish text\.   
HTTP Status Code: 400

## See Also<a name="API_BatchDetectSyntax_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/BatchDetectSyntax) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/BatchDetectSyntax) 