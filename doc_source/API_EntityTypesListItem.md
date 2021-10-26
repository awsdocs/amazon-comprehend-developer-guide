# EntityTypesListItem<a name="API_EntityTypesListItem"></a>

An entity type within a labeled training dataset that Amazon Comprehend uses to train a custom entity recognizer\.

## Contents<a name="API_EntityTypesListItem_Contents"></a>

 ** Type **   <a name="comprehend-Type-EntityTypesListItem-Type"></a>
An entity type within a labeled training dataset that Amazon Comprehend uses to train a custom entity recognizer\.  
Entity types must not contain the following invalid characters: \\n \(line break\), \\\\n \(escaped line break, \\r \(carriage return\), \\\\r \(escaped carriage return\), \\t \(tab\), \\\\t \(escaped tab\), space, and , \(comma\)\.  
Type: String  
Length Constraints: Maximum length of 64\.  
Pattern: `^(?:(?!\\n+|\\t+|\\r+|[\r\t\n,]).)+$`   
Required: Yes

## See Also<a name="API_EntityTypesListItem_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityTypesListItem) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityTypesListItem) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityTypesListItem) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityTypesListItem) 