# RedactionConfig<a name="API_RedactionConfig"></a>

Provides configuration parameters for PII entity redaction\.

## Contents<a name="API_RedactionConfig_Contents"></a>

 ** MaskCharacter **   <a name="comprehend-Type-RedactionConfig-MaskCharacter"></a>
A character that replaces each character in the redacted PII entity\.  
Type: String  
Length Constraints: Fixed length of 1\.  
Pattern: `[!@#$%&*]`   
Required: No

 ** MaskMode **   <a name="comprehend-Type-RedactionConfig-MaskMode"></a>
Specifies whether the PII entity is redacted with the mask character or the entity type\.  
Type: String  
Valid Values:` MASK | REPLACE_WITH_PII_ENTITY_TYPE`   
Required: No

 ** PiiEntityTypes **   <a name="comprehend-Type-RedactionConfig-PiiEntityTypes"></a>
An array of the types of PII entities that Amazon Comprehend detects in the input text for your request\.  
Type: Array of strings  
Valid Values:` BANK_ACCOUNT_NUMBER | BANK_ROUTING | CREDIT_DEBIT_NUMBER | CREDIT_DEBIT_CVV | CREDIT_DEBIT_EXPIRY | PIN | EMAIL | ADDRESS | NAME | PHONE | SSN | DATE_TIME | PASSPORT_NUMBER | DRIVER_ID | URL | AGE | USERNAME | PASSWORD | AWS_ACCESS_KEY | AWS_SECRET_KEY | IP_ADDRESS | MAC_ADDRESS | ALL`   
Required: No

## See Also<a name="API_RedactionConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/RedactionConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/RedactionConfig) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/RedactionConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/RedactionConfig) 