# BatchDetectDominantLanguageItemResult<a name="API_BatchDetectDominantLanguageItemResult"></a>

The result of calling the [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) operation\. The operation returns one object for each document that is successfully processed by the operation\.

## Contents<a name="API_BatchDetectDominantLanguageItemResult_Contents"></a>

 **Index**   <a name="comprehend-Type-BatchDetectDominantLanguageItemResult-Index"></a>
The zero\-based index of the document in the input list\.  
Type: Integer  
Required: No

 **Languages**   <a name="comprehend-Type-BatchDetectDominantLanguageItemResult-Languages"></a>
One or more [DominantLanguage](API_DominantLanguage.md) objects describing the dominant languages in the document\.  
Type: Array of [DominantLanguage](API_DominantLanguage.md) objects  
Required: No

## See Also<a name="API_BatchDetectDominantLanguageItemResult_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectDominantLanguageItemResult) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectDominantLanguageItemResult) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/BatchDetectDominantLanguageItemResult) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/BatchDetectDominantLanguageItemResult) 