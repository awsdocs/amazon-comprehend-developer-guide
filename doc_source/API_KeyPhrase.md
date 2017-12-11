# KeyPhrase<a name="API_KeyPhrase"></a>

Describes a key noun phrase\.

## Contents<a name="API_KeyPhrase_Contents"></a>

 **BeginOffset**   
A character offset in the input text that shows where the key phrase begins \(the first character is at position 0\)\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 **EndOffset**   
A character offset in the input text where the key phrase ends\. The offset returns the position of each UTF\-8 code point in the string\. A `code point` is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 **Score**   
The level of confidence that Amazon Comprehend has in the accuracy of the detection\.  
Type: Float  
Required: No

 **Text**   
The text of a key noun phrase\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

## See Also<a name="API_KeyPhrase_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/KeyPhrase) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/KeyPhrase) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/KeyPhrase) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/KeyPhrase) 