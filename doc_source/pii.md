# Personally identifiable information \(PII\)<a name="pii"></a>

You can use the Amazon Comprehend console or APIs to detect *personally identifiable information \(PII\)* in English text documents\. PII is a textual reference to personal data that could be used to identify an individual\. PII examples include addresses, bank account numbers, and phone numbers\.

With PII detection, you have the choice of locating the PII entities or redacting the PII entities in the text\. To locate PII entities, you can use real\-time analysis or an asynchronous batch job\. To redact the PII entities, you must use an asynchronous batch job\.

You can use Amazon S3 Object Lambda Access Points for personally identifiable information \(PII\) to control the retrieval of documents from your Amazon S3 bucket\. You can control access to documents that contain PII and redact personally identifiable information from the documents\. For more information, see [Using Amazon S3 object Lambda access points for personally identifiable information \(PII\)](using-access-points.md)\.

**Topics**
+ [Detecting PII entities](how-pii.md)
+ [Labeling PII entities](how-pii-labels.md)
+ [PII real\-time analysis \(Console\)](realtime-pii-console.md)
+ [PII asynchronous analysis jobs \(Console\)](async-pii-console.md)
+ [PII real\-time analysis \(API\)](realtime-pii-api.md)
+ [PII asynchronous analysis jobs \(API\)](get-started-api-pii.md)