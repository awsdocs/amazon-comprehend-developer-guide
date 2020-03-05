# RxNormAttribute<a name="API_medical_RxNormAttribute"></a>

The extracted attributes that relate to this entity\. The attributes recognized by InferRxNorm are `DOSAGE`, `DURATION`, `FORM`, `FREQUENCY`, `RATE`, `ROUTE_OR_MODE`\.

## Contents<a name="API_medical_RxNormAttribute_Contents"></a>

 **BeginOffset**   <a name="comprehend-Type-medical_RxNormAttribute-BeginOffset"></a>
The 0\-based character offset in the input text that shows where the attribute begins\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **EndOffset**   <a name="comprehend-Type-medical_RxNormAttribute-EndOffset"></a>
The 0\-based character offset in the input text that shows where the attribute ends\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **Id**   <a name="comprehend-Type-medical_RxNormAttribute-Id"></a>
The numeric identifier for this attribute\. This is a monotonically increasing id unique within this response rather than a global unique identifier\.  
Type: Integer  
Required: No

 **RelationshipScore**   <a name="comprehend-Type-medical_RxNormAttribute-RelationshipScore"></a>
The level of confidence that Amazon Comprehend Medical has that the attribute is accurately linked to an entity\.  
Type: Float  
Required: No

 **Score**   <a name="comprehend-Type-medical_RxNormAttribute-Score"></a>
The level of confidence that Comprehend Medical has that the segment of text is correctly recognized as an attribute\.  
Type: Float  
Required: No

 **Text**   <a name="comprehend-Type-medical_RxNormAttribute-Text"></a>
The segment of input text which corresponds to the detected attribute\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Traits**   <a name="comprehend-Type-medical_RxNormAttribute-Traits"></a>
Contextual information for the attribute\. InferRxNorm recognizes the trait `NEGATION` for attributes, i\.e\. that the patient is not taking a specific dose or form of a medication\.  
Type: Array of [RxNormTrait](API_medical_RxNormTrait.md) objects  
Required: No

 **Type**   <a name="comprehend-Type-medical_RxNormAttribute-Type"></a>
The type of attribute\. The types of attributes recognized by InferRxNorm are `BRAND_NAME` and `GENERIC_NAME`\.  
Type: String  
Valid Values:` DOSAGE | DURATION | FORM | FREQUENCY | RATE | ROUTE_OR_MODE | STRENGTH`   
Required: No

## See Also<a name="API_medical_RxNormAttribute_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/RxNormAttribute) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/RxNormAttribute) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/RxNormAttribute) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/RxNormAttribute) 