# Running asynchronous jobs<a name="running-classifiers"></a>

After you train a custom classifier, you can use asynchronous jobs to analyze large documents or multiple documents in one batch\.

Custom classification accepts a variety of input document types\. For details, see [Inputs for asynchronous custom analysis](idp-inputs-async.md)\.

If you plan to analyze image files or scanned PDF documents, your IAM policy must grant permissions to use two Amazon Textract API methods \(DetectDocumentText and AnalyzeDocument\)\. Amazon Comprehend invokes these methods during text extraction\. For an example policy, see [Using identity\-based policies \(IAM policies\) for Amazon Comprehend](access-control-managing-permissions.md)\.

For classification of semi\-structured documents \(image, PDF, or Docx files\) using a plain\-text classifier, use the `one document per file` input format\. Also, include the `DocumentReaderConfig` parameter in your [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html) request\.

**Topics**
+ [File formats for async analysis](class-inputs-async.md)
+ [Analysis jobs for custom classification \(console\)](analysis-jobs-custom-classifier.md)
+ [Analysis jobs for custom classification \(API\)](analysis-jobs-custom-class-api.md)
+ [Outputs for asynchronous analysis jobs](outputs-class-async.md)