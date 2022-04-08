# EntityLabel<a name="API_EntityLabel"></a>

Specifies one of the label or labels that categorize the personally identifiable information \(PII\) entity being analyzed\.

## Contents<a name="API_EntityLabel_Contents"></a>

 ** Name **   <a name="comprehend-Type-EntityLabel-Name"></a>
The name of the label\.  
Type: String  
Valid Values:` BANK_ACCOUNT_NUMBER | BANK_ROUTING | CREDIT_DEBIT_NUMBER | CREDIT_DEBIT_CVV | CREDIT_DEBIT_EXPIRY | PIN | EMAIL | ADDRESS | NAME | PHONE | SSN | DATE_TIME | PASSPORT_NUMBER | DRIVER_ID | URL | AGE | USERNAME | PASSWORD | AWS_ACCESS_KEY | AWS_SECRET_KEY | IP_ADDRESS | MAC_ADDRESS`   
Required: Yes

 ** Score **   <a name="comprehend-Type-EntityLabel-Score"></a>
The level of confidence that Amazon Comprehend has in the accuracy of the detection\.  
Type: Float  
Required: Yes

## See Also<a name="API_EntityLabel_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityLabel) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityLabel) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityLabel) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityLabel) 