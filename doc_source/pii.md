# Personally identifiable information \(PII\)<a name="pii"></a>

You can use Amazon Comprehend to detect entities in your text that contain personally identifiable information \(PII\)\. When Amazon Comprehend completes its analysis, it returns output that either locates or redacts the PII entities in the text\.

For example, you can detect the PII entities in the following text by submitting it to Amazon Comprehend:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

If you choose to locate the PII entities, the output includes the character offsets for each one, along with the entity type and other details\. In this case, the output states that "Paul Santos" has the type `NAME`, "1111\-0000\-1111\-0000" has the type `CREDIT_DEBIT_NUMBER`, and "123 Any Street, Seattle, WA 98109" has the type `ADDRESS`\.

Alternatively, if you choose to redact the PII entities, Amazon Comprehend returns a copy of the input text in which each PII entity is redacted:

*Hello \*\*\*\*\* \*\*\*\*\*\*\. The latest statement for your credit card account \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* was mailed to \*\*\* \*\*\* \*\*\*\*\*\*\* \*\*\*\*\*\*\*\* \*\* \*\*\*\*\*\.*

You can detect PII entities with both real\-time synchronous operations and batch asynchronous jobs\. However, you must use an asynchronous job if you want to produce output with redacted PII entities\. 

You can use Amazon S3 Object Lambda Access Points for personally identifiable information \(PII\) to control the retrieval of documents from your Amazon S3 bucket\. You can control access to documents that contain PII and redact personally identifiable information from the documents\. For more information, see [Using Amazon S3 object Lambda access points for personally identifiable information \(PII\)](using-access-points.md)\.

**Topics**
+ [PII entities](how-pii.md)
+ [Detect PII using the API](get-started-api-pii.md)
+ [Labeling documents with PII](how-pii-labels.md)
+ [Labeling documents with PII \(API\)](get-started-api-pii-labels.md)