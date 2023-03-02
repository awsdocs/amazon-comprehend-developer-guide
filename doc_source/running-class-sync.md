# Running real\-time analysis<a name="running-class-sync"></a>

After you train a custom classifier, you can classify documents using real\-time analysis\. Real\-time analysis takes a single document as input and returns the results synchronously\. Custom classification accepts a variety of document types as inputs for real\-time analysis\. For details, see [Inputs for real\-time custom analysis](idp-inputs-sync.md)\.

If you plan to analyze image files or scanned PDF documents, your IAM policy must grant permissions to use two Amazon Textract API methods \(DetectDocumentText and AnalyzeDocument\)\. Amazon Comprehend invokes these methods during text extraction\. For an example policy, see [ Permissions required to perform document analysis actions](security_iam_id-based-policy-examples.md#security-iam-based-policy-perform-cmp-actions)\.

You must create an endpoint to run real\-time analysis using a custom classification model\. 

**Topics**
+ [Real\-time analysis for custom classification \(console\)](custom-sync.md)
+ [Real\-time analysis for custom classification \(API\)](class-sync-api.md)
+ [Outputs for real\-time analysis](outputs-class-sync.md)