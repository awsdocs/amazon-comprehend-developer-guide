# ICD10CMEntity<a name="API_medical_ICD10CMEntity"></a>

The collection of medical entities extracted from the input text and their associated information\. For each entity, the response provides the entity text, the entity category, where the entity text begins and ends, and the level of confidence that Amazon Comprehend Medical has in the detection and analysis\. Attributes and traits of the entity are also returned\. 

## Contents<a name="API_medical_ICD10CMEntity_Contents"></a>

 **Attributes**   <a name="comprehend-Type-medical_ICD10CMEntity-Attributes"></a>
The detected attributes that relate to the entity\. An extracted segment of the text that is an attribute of an entity, or otherwise related to an entity, such as the nature of a medical condition\.  
Type: Array of [ICD10CMAttribute](API_medical_ICD10CMAttribute.md) objects  
Required: No

 **BeginOffset**   <a name="comprehend-Type-medical_ICD10CMEntity-BeginOffset"></a>
The 0\-based character offset in the input text that shows where the entity begins\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **Category**   <a name="comprehend-Type-medical_ICD10CMEntity-Category"></a>
 The category of the entity\. InferICD10CM detects entities in the `MEDICAL_CONDITION` category\.   
Type: String  
Valid Values:` MEDICAL_CONDITION`   
Required: No

 **EndOffset**   <a name="comprehend-Type-medical_ICD10CMEntity-EndOffset"></a>
The 0\-based character offset in the input text that shows where the entity ends\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **ICD10CMConcepts**   <a name="comprehend-Type-medical_ICD10CMEntity-ICD10CMConcepts"></a>
The ICD\-10\-CM concepts that the entity could refer to, along with a score indicating the likelihood of the match\.  
Type: Array of [ICD10CMConcept](API_medical_ICD10CMConcept.md) objects  
Required: No

 **Id**   <a name="comprehend-Type-medical_ICD10CMEntity-Id"></a>
The numeric identifier for the entity\. This is a monotonically increasing id unique within this response rather than a global unique identifier\.  
Type: Integer  
Required: No

 **Score**   <a name="comprehend-Type-medical_ICD10CMEntity-Score"></a>
The level of confidence that Amazon Comprehend Medical has in the accuracy of the detection\.  
Type: Float  
Required: No

 **Text**   <a name="comprehend-Type-medical_ICD10CMEntity-Text"></a>
The segment of input text that is matched to the detected entity\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 10000\.  
Required: No

 **Traits**   <a name="comprehend-Type-medical_ICD10CMEntity-Traits"></a>
Provides Contextual information for the entity\. The traits recognized by InferICD10CM are `DIAGNOSIS`, `SIGN`, `SYMPTOM`, and `NEGATION.`   
Type: Array of [ICD10CMTrait](API_medical_ICD10CMTrait.md) objects  
Required: No

 **Type**   <a name="comprehend-Type-medical_ICD10CMEntity-Type"></a>
Describes the specific type of entity with category of entities\. InferICD10CM detects entities of the type `DX_NAME`\.  
Type: String  
Valid Values:` DX_NAME`   
Required: No

## See Also<a name="API_medical_ICD10CMEntity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/ICD10CMEntity) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/ICD10CMEntity) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/ICD10CMEntity) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/ICD10CMEntity) 