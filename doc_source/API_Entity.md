# Entity<a name="API_Entity"></a>

Provides information about an entity\. 

 

## Contents<a name="API_Entity_Contents"></a>

 **BeginOffset**   
A character offset in the input text that shows where the entity begins \(the first character is at position 0\)\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 **EndOffset**   
A character offset in the input text that shows where the entity ends\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.   
Type: Integer  
Required: No

 **Score**   
The level of confidence that Amazon Comprehend has in the accuracy of the detection\.  
Type: Float  
Required: No

 **Text**   
The text of the entity\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Type**   
The entity's type\.  
Type: String  
Valid Values:` PERSON | LOCATION | ORGANIZATION | COMMERCIAL_ITEM | EVENT | DATE | QUANTITY | TITLE | OTHER`   
Required: No

## See Also<a name="API_Entity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/Entity) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/Entity) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/Entity) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/Entity) 