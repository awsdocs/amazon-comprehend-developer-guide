# Entity<a name="API_Entity"></a>

Provides information about an entity\. 

 

## Contents<a name="API_Entity_Contents"></a>

 **BeginOffset**   <a name="comprehend-Type-Entity-BeginOffset"></a>
A character offset in the input text that shows where the entity begins \(the first character is at position 0\)\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 **EndOffset**   <a name="comprehend-Type-Entity-EndOffset"></a>
A character offset in the input text that shows where the entity ends\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.   
Type: Integer  
Required: No

 **Score**   <a name="comprehend-Type-Entity-Score"></a>
The level of confidence that Amazon Comprehend has in the accuracy of the detection\.  
Type: Float  
Required: No

 **Text**   <a name="comprehend-Type-Entity-Text"></a>
The text of the entity\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Type**   <a name="comprehend-Type-Entity-Type"></a>
The entity's type\.  
Type: String  
Valid Values:` PERSON | LOCATION | ORGANIZATION | COMMERCIAL_ITEM | EVENT | DATE | QUANTITY | TITLE | OTHER`   
Required: No

## See Also<a name="API_Entity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/Entity) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/Entity) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/Entity) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/Entity) 