# RxNormEntity<a name="API_medical_RxNormEntity"></a>

The collection of medical entities extracted from the input text and their associated information\. For each entity, the response provides the entity text, the entity category, where the entity text begins and ends, and the level of confidence that Amazon Comprehend Medical has in the detection and analysis\. Attributes and traits of the entity are also returned\. 

## Contents<a name="API_medical_RxNormEntity_Contents"></a>

 **Attributes**   <a name="comprehend-Type-medical_RxNormEntity-Attributes"></a>
The extracted attributes that relate to the entity\. The attributes recognized by InferRxNorm are `DOSAGE`, `DURATION`, `FORM`, `FREQUENCY`, `RATE`, `ROUTE_OR_MODE`, and `STRENGTH`\.  
Type: Array of [RxNormAttribute](API_medical_RxNormAttribute.md) objects  
Required: No

 **BeginOffset**   <a name="comprehend-Type-medical_RxNormEntity-BeginOffset"></a>
The 0\-based character offset in the input text that shows where the entity begins\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **Category**   <a name="comprehend-Type-medical_RxNormEntity-Category"></a>
The category of the entity\. The recognized categories are `GENERIC` or `BRAND_NAME`\.  
Type: String  
Valid Values:` MEDICATION`   
Required: No

 **EndOffset**   <a name="comprehend-Type-medical_RxNormEntity-EndOffset"></a>
The 0\-based character offset in the input text that shows where the entity ends\. The offset returns the UTF\-8 code point in the string\.  
Type: Integer  
Required: No

 **Id**   <a name="comprehend-Type-medical_RxNormEntity-Id"></a>
The numeric identifier for the entity\. This is a monotonically increasing id unique within this response rather than a global unique identifier\.  
Type: Integer  
Required: No

 **RxNormConcepts**   <a name="comprehend-Type-medical_RxNormEntity-RxNormConcepts"></a>
 The RxNorm concepts that the entity could refer to, along with a score indicating the likelihood of the match\.  
Type: Array of [RxNormConcept](API_medical_RxNormConcept.md) objects  
Required: No

 **Score**   <a name="comprehend-Type-medical_RxNormEntity-Score"></a>
The level of confidence that Amazon Comprehend Medical has in the accuracy of the detected entity\.  
Type: Float  
Required: No

 **Text**   <a name="comprehend-Type-medical_RxNormEntity-Text"></a>
The segment of input text extracted from which the entity was detected\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 10000\.  
Required: No

 **Traits**   <a name="comprehend-Type-medical_RxNormEntity-Traits"></a>
 Contextual information for the entity\.  
Type: Array of [RxNormTrait](API_medical_RxNormTrait.md) objects  
Required: No

 **Type**   <a name="comprehend-Type-medical_RxNormEntity-Type"></a>
 Describes the specific type of entity\. For InferRxNorm, the recognized entity type is `MEDICATION`\.  
Type: String  
Valid Values:` BRAND_NAME | GENERIC_NAME`   
Required: No

## See Also<a name="API_medical_RxNormEntity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/RxNormEntity) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/RxNormEntity) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/RxNormEntity) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/RxNormEntity) 