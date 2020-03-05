# Entity<a name="API_medical_Entity"></a>

 Provides information about an extracted medical entity\.

## Contents<a name="API_medical_Entity_Contents"></a>

 **Attributes**   <a name="comprehend-Type-medical_Entity-Attributes"></a>
 The extracted attributes that relate to this entity\.  
Type: Array of [Attribute](API_medical_Attribute.md) objects  
Required: No

 **BeginOffset**   <a name="comprehend-Type-medical_Entity-BeginOffset"></a>
 The 0\-based character offset in the input text that shows where the entity begins\. The offset returns the UTF\-8 code point in the string\.   
Type: Integer  
Required: No

 **Category**   <a name="comprehend-Type-medical_Entity-Category"></a>
 The category of the entity\.  
Type: String  
Valid Values:` MEDICATION | MEDICAL_CONDITION | PROTECTED_HEALTH_INFORMATION | TEST_TREATMENT_PROCEDURE | ANATOMY | TIME_EXPRESSION`   
Required: No

 **EndOffset**   <a name="comprehend-Type-medical_Entity-EndOffset"></a>
 The 0\-based character offset in the input text that shows where the entity ends\. The offset returns the UTF\-8 code point in the string\.   
Type: Integer  
Required: No

 **Id**   <a name="comprehend-Type-medical_Entity-Id"></a>
 The numeric identifier for the entity\. This is a monotonically increasing id unique within this response rather than a global unique identifier\.   
Type: Integer  
Required: No

 **Score**   <a name="comprehend-Type-medical_Entity-Score"></a>
The level of confidence that Amazon Comprehend Medical has in the accuracy of the detection\.  
Type: Float  
Required: No

 **Text**   <a name="comprehend-Type-medical_Entity-Text"></a>
 The segment of input text extracted as this entity\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Traits**   <a name="comprehend-Type-medical_Entity-Traits"></a>
Contextual information for the entity\.  
Type: Array of [Trait](API_medical_Trait.md) objects  
Required: No

 **Type**   <a name="comprehend-Type-medical_Entity-Type"></a>
 Describes the specific type of entity with category of entities\.  
Type: String  
Valid Values:` NAME | DOSAGE | ROUTE_OR_MODE | FORM | FREQUENCY | DURATION | GENERIC_NAME | BRAND_NAME | STRENGTH | RATE | ACUITY | TEST_NAME | TEST_VALUE | TEST_UNITS | PROCEDURE_NAME | TREATMENT_NAME | DATE | AGE | CONTACT_POINT | EMAIL | IDENTIFIER | URL | ADDRESS | PROFESSION | SYSTEM_ORGAN_SITE | DIRECTION | QUALITY | QUANTITY | TIME_EXPRESSION | TIME_TO_MEDICATION_NAME | TIME_TO_DX_NAME | TIME_TO_TEST_NAME | TIME_TO_PROCEDURE_NAME | TIME_TO_TREATMENT_NAME`   
Required: No

## See Also<a name="API_medical_Entity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/Entity) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/Entity) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/Entity) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/Entity) 