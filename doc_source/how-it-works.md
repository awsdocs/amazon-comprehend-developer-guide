# How it works<a name="how-it-works"></a>

Amazon Comprehend uses a pre\-trained model to gather **insights** about a document or a set of documents\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. 

You can use Amazon Comprehend to build your own **custom models** for custom classification and custom entity recognition\. 

Amazon Comprehend provides **topic modeling** using a built\-in model\. Topic modeling examines a corpus of documents and organizes the documents based on similar keywords within them\.

Amazon Comprehend provides synchronous and asynchronous **document processing modes**\. Use synchronous mode for processing one document or a batch of up to 25 documents\. Use an asynchronous job to process a large number of documents\.

Amazon Comprehend works with AWS Key Management Service \(AWS KMS\) to provide enhanced encryption for your data\. For more information, see [KMS encryption in Amazon Comprehend](kms-in-comprehend.md)\.



**Topics**
+ [Insights](concepts-insights.md)
+ [Amazon Comprehend Custom](concepts-custom.md)
+ [Topic modeling](topic-modeling.md)
+ [Document processing modes](concepts-processing-modes.md)