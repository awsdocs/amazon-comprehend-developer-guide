# SyntaxToken<a name="API_SyntaxToken"></a>

Represents a work in the input text that was recognized and assigned a part of speech\. There is one syntax token record for each word in the source text\.

## Contents<a name="API_SyntaxToken_Contents"></a>

 ** BeginOffset **   <a name="comprehend-Type-SyntaxToken-BeginOffset"></a>
The zero\-based offset from the beginning of the source text to the first character in the word\.  
Type: Integer  
Required: No

 ** EndOffset **   <a name="comprehend-Type-SyntaxToken-EndOffset"></a>
The zero\-based offset from the beginning of the source text to the last character in the word\.  
Type: Integer  
Required: No

 ** PartOfSpeech **   <a name="comprehend-Type-SyntaxToken-PartOfSpeech"></a>
Provides the part of speech label and the confidence level that Amazon Comprehend has that the part of speech was correctly identified\. For more information, see [Analyze Syntax](how-syntax.md)\.  
Type: [ PartOfSpeechTag ](API_PartOfSpeechTag.md) object  
Required: No

 ** Text **   <a name="comprehend-Type-SyntaxToken-Text"></a>
The word that was recognized in the source text\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 ** TokenId **   <a name="comprehend-Type-SyntaxToken-TokenId"></a>
A unique identifier for a token\.  
Type: Integer  
Required: No

## See Also<a name="API_SyntaxToken_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/SyntaxToken) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/SyntaxToken) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/SyntaxToken) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/SyntaxToken) 