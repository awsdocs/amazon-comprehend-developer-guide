# Running analysis jobs for custom entity recognition<a name="detecting-cer"></a>

You can run an asynchronous analysis job to detect custom entities in a set of one or more documents\.

**Before you begin**  
You need a custom entity recognition model \(also known as a recognizer\) before you can detect custom entities\. For more information about these models, see [Training custom recognizers](training-recognizers.md)\. 

A recognizer that is trained with plain\-text annotations supports entity detection for plain\-text documents only\. A recognizer that is trained with PDF document annotations supports entity detection for plain\-text documents, images, PDF files, and Word documents\. For files other than text files, Amazon Comprehend performs text extraction before running the analysis\. For information about the input files, see [Inputs for asynchronous custom analysis](idp-inputs-async.md)\.

If you plan to analyze image files or scanned PDF documents, your IAM policy must grant permissions to use two Amazon Textract API methods \(DetectDocumentText and AnalyzeDocument\)\. Amazon Comprehend invokes these methods during text extraction\. For an example policy, see [Using identity\-based policies \(IAM policies\) for Amazon Comprehend](access-control-managing-permissions.md)\.

To run an async analysis job, you perform the following overall steps:

1. Store the documents in an Amazon S3 bucket\.

1. Use the API or console to start the analysis job\.

1. Monitor the progress of the analysis job\.

1. After the job runs to completion, retrieve the results of the analysis from the S3 bucket that you specified when you started the job\.

**Topics**
+ [Starting a custom entity detection job \(console\)](detecting-cer-async-console.md)
+ [Starting a custom entity detection job \(API\)](detecting-cer-async-api.md)
+ [Outputs for asynchronous analysis jobs](outputs-cer-async.md)