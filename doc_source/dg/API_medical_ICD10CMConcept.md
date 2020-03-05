# ICD10CMConcept<a name="API_medical_ICD10CMConcept"></a>

 The ICD\-10\-CM concepts that the entity could refer to, along with a score indicating the likelihood of the match\.

## Contents<a name="API_medical_ICD10CMConcept_Contents"></a>

 **Code**   <a name="comprehend-Type-medical_ICD10CMConcept-Code"></a>
The ICD\-10\-CM code that identifies the concept found in the knowledge base from the Centers for Disease Control\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Description**   <a name="comprehend-Type-medical_ICD10CMConcept-Description"></a>
The long description of the ICD\-10\-CM code in the ontology\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: No

 **Score**   <a name="comprehend-Type-medical_ICD10CMConcept-Score"></a>
The level of confidence that Amazon Comprehend Medical has that the entity is accurately linked to an ICD\-10\-CM concept\.  
Type: Float  
Required: No

## See Also<a name="API_medical_ICD10CMConcept_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/ICD10CMConcept) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/ICD10CMConcept) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/ICD10CMConcept) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/ICD10CMConcept) 