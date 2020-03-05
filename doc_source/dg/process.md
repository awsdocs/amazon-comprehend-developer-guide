# Document Processing Modes<a name="process"></a>

Amazon Comprehend enables you to examine your documents to gain various insights about their content\. 

When evaluating your documents, you can use one of several methods to process them, depending on how many documents you have and how you want to view the results:
+ [Single\-Document Processing](how-single.md)—You call Amazon Comprehend with a single document and receive a synchronous response, delivered to your application right away\. 
+ [Multiple Document Synchronous Processing](how-batch.md)—You call Amazon Comprehend with a collection of up to 25 documents and receive a synchronous response\.
+ [Asynchronous Batch Processing](how-async.md)—You put a collection of documents into an Amazon S3 bucket and start an asynchronous operation to analyze the documents\. The results of the analysis are returned in an S3 bucket\.