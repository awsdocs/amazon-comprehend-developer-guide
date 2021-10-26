# BatchDetectKeyPhrasesItemResult<a name="API_BatchDetectKeyPhrasesItemResult"></a>

The result of calling the [ BatchDetectKeyPhrases ](API_BatchDetectKeyPhrases.md) operation\. The operation returns one object for each document that is successfully processed by the operation\.

## Contents<a name="API_BatchDetectKeyPhrasesItemResult_Contents"></a>

 ** Index **   <a name="comprehend-Type-BatchDetectKeyPhrasesItemResult-Index"></a>
The zero\-based index of the document in the input list\.  
Type: Integer  
Required: No

 ** KeyPhrases **   <a name="comprehend-Type-BatchDetectKeyPhrasesItemResult-KeyPhrases"></a>
One or more [ KeyPhrase ](API_KeyPhrase.md) objects, one for each key phrase detected in the document\.  
Type: Array of [ KeyPhrase ](API_KeyPhrase.md) objects  
Required: No

## See Also<a name="API_BatchDetectKeyPhrasesItemResult_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectKeyPhrasesItemResult) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectKeyPhrasesItemResult) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/BatchDetectKeyPhrasesItemResult) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/BatchDetectKeyPhrasesItemResult) 