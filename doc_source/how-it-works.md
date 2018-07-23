# How It Works<a name="how-it-works"></a>

Amazon Comprehend uses a pre\-trained model to examine a document or set of documents to gather insights about the document set\. The model is continuously trained on a large body of text so that there is no need for you to provide training data\. Except for the [DetectDominantLanguage](API_DetectDominantLanguage.md) operation, Amazon Comprehend can examine documents in these languages:
+ English
+ Spanish

Amazon Comprehend provides the following operations:
+ [Single\-Document Processing](how-single.md)—You call Amazon Comprehend with a single document and receive a synchronous response\. 
+ [Multiple Document Synchronous Processing](how-batch.md)—You call Amazon Comprehend with a collection of up to 25 documents and receive a synchronous response\.
+ [Asynchronous Batch Processing](how-async.md)—You put a collection of documents into an Amazon S3 bucket and start an asynchronous operation to analyze the documents\. The results of the analysis are returned in an S3 bucket\.