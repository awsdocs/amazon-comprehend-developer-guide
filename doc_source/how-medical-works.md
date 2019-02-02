# How It Works<a name="how-medical-works"></a>

Comprehend Medical uses the [DetectEntities](API_hera_DetectEntities.md) and [DetectPHI](API_hera_DetectPHI.md) operations to detect valuable information in unstructured clinical text\. 

Amazon Comprehend Medical uses a pre\-trained model to examine and analyze a document or set of documents to gather insights about it\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. Amazon Comprehend Medical can examine and analyze documents in English\.

With Amazon Comprehend Medical, you can perform the following operations on your documents:
+ [Detect Entities](extracted-med-info.md)—Examine unstructured clinical text to detect textual references to valuable medical information such as medical condition, treatment, tests and test results, medication \(including dosage, frequency, method of administration, and so on\), treatment, PHI data, and so on\.
+ [Detect PHI ](how-medical-phi.md)—Examine unstructured clinical text to detect textual references to protected health information \(PHI\) such as names and addresses\.

Each operation processes a single document synchronously\.