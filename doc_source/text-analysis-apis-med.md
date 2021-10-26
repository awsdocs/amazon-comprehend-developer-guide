# Text Analysis APIs<a name="text-analysis-apis-med"></a>

Amazon Comprehend Medical enables you to examine clinical documents to gain various insights about their content using pre\-trained Natural Language Processing \(NLP\) models\. 

With Amazon Comprehend Medical, you can perform the following on your documents:
+ [Detect Entities Version 2](extracted-med-info-V2.md)—Examine unstructured clinical text to detect textual references to medical information such as medical condition, treatment, tests and results, and medications\. This version uses a new model and changes the way some entities are returned in the output\. For more information, see [DetectEntitiesV2](API_medical_DetectEntitiesV2.md)\.
+ [Detect PHI ](how-medical-phi.md)—Examine unstructured clinical text to detect textual references to protected health information \(PHI\) such as names and addresses\.
+ [Detect Entities](extracted-med-info.md)— Examine unstructured clinical text to detect textual references to medical information such as medical condition, treatment, tests and results, and medications\. Use `Detect Entities Version 2 ` for all new applications\.

**Topics**
+ [Detect Entities Version 2](extracted-med-info-V2.md)
+ [Detect Entities](extracted-med-info.md)
+ [Detect PHI](how-medical-phi.md)
+ [Batch APIs](batch-api-med.md)