# PiiEntity<a name="API_PiiEntity"></a>

Provides information about a PII entity\.

## Contents<a name="API_PiiEntity_Contents"></a>

 ** BeginOffset **   <a name="comprehend-Type-PiiEntity-BeginOffset"></a>
A character offset in the input text that shows where the PII entity begins \(the first character is at position 0\)\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 ** EndOffset **   <a name="comprehend-Type-PiiEntity-EndOffset"></a>
A character offset in the input text that shows where the PII entity ends\. The offset returns the position of each UTF\-8 code point in the string\. A *code point* is the abstract character from a particular graphical representation\. For example, a multi\-byte UTF\-8 character maps to a single code point\.  
Type: Integer  
Required: No

 ** Score **   <a name="comprehend-Type-PiiEntity-Score"></a>
The level of confidence that Amazon Comprehend has in the accuracy of the detection\.  
Type: Float  
Required: No

 ** Type **   <a name="comprehend-Type-PiiEntity-Type"></a>
The entity's type\.  
Type: String  
Valid Values:` BANK_ACCOUNT_NUMBER | BANK_ROUTING | CREDIT_DEBIT_NUMBER | CREDIT_DEBIT_CVV | CREDIT_DEBIT_EXPIRY | PIN | EMAIL | ADDRESS | NAME | PHONE | SSN | DATE_TIME | PASSPORT_NUMBER | DRIVER_ID | URL | AGE | USERNAME | PASSWORD | AWS_ACCESS_KEY | AWS_SECRET_KEY | IP_ADDRESS | MAC_ADDRESS | LICENSE_PLATE | VEHICLE_IDENTIFICATION_NUMBER | UK_NATIONAL_INSURANCE_NUMBER | CA_SOCIAL_INSURANCE_NUMBER | US_INDIVIDUAL_TAX_IDENTIFICATION_NUMBER | UK_UNIQUE_TAXPAYER_REFERENCE_NUMBER | IN_PERMANENT_ACCOUNT_NUMBER | IN_NREGA | INTERNATIONAL_BANK_ACCOUNT_NUMBER | SWIFT_CODE | UK_NATIONAL_HEALTH_SERVICE_NUMBER | CA_HEALTH_NUMBER | IN_AADHAAR | IN_VOTER_NUMBER | ALL`   
Required: No

## See Also<a name="API_PiiEntity_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/PiiEntity) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/PiiEntity) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/PiiEntity) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/PiiEntity) 