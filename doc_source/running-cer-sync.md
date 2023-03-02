# Running real\-time custom recognizer analysis<a name="running-cer-sync"></a>

Real\-time analysis is useful for applications that process small documents as they arrive\. For example, you can detect custom entities in social media posts, support tickets, or customer reviews\. 

**Before you begin**  
You need a custom entity recognition model \(also known as a recognizer\) before you can detect custom entities\. For more information about these models, see [Training custom entity recognizer models](training-recognizers.md)\. 

A recognizer that is trained with plain\-text annotations supports entity detection for plain\-text documents only\. A recognizer that is trained with PDF document annotations supports entity detection for plain\-text documents, images, PDF files, and Word documents\. For information about the input files, see [Inputs for real\-time custom analysis](idp-inputs-sync.md)\.

If you plan to analyze image files or scanned PDF documents, your IAM policy must grant permissions to use two Amazon Textract API methods \(DetectDocumentText and AnalyzeDocument\)\. Amazon Comprehend invokes these methods during text extraction\. For an example policy, see [ Permissions required to perform document analysis actions](security_iam_id-based-policy-examples.md#security-iam-based-policy-perform-cmp-actions)\.

**Topics**
+ [Real\-time analysis for custom entity recognition \(console\)](detecting-cer-real-time.md)
+ [Real\-time analysis for custom entity recognition \(API\)](detecting-cer-real-time-api.md)
+ [Outputs for real\-time analysis](outputs-cer-sync.md)