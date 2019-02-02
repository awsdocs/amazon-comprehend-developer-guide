# How It Works<a name="how-it-works"></a>

Amazon Comprehend uses a pre\-trained model to examine and analyze a document or set of documents to gather insights about it\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. 

Amazon Comprehend can examine and analyze documents in these languages: 
+ English
+ Spanish
+ French
+ German
+ Italian
+ Portuguese

Additionally, Amazon Comprehend's [Detect the Dominant Language](how-languages.md) operation can examine documents and determine the dominant language out of a far wider variety of different languages\. For more information, see [Languages Supported in Amazon Comprehend](supported-languages.md)\.

With Amazon Comprehend, you can perform the following on your documents:
+ [Detect the Dominant Language](how-languages.md)—Examine text to determine the dominant language\.
+ [Detect Entities](how-entities.md)—Detect textual references to the names of people, places, and items as well as references to dates and quantities\.
+ [Locate Key Phrases](how-key-phrases.md)—Find key phrases such as "good morning" in a document or set of documents\.
+ [Determine the Sentiment](how-sentiment.md)—Analyze documents and determine the dominant sentiment of the text\.
+ [Analyze Syntax](how-syntax.md)—Parse the words in your text and show the speech syntax for each word and enable you to understand the content of the document\.
+ [Topic Modeling](topic-modeling.md)—Search the content of documents to determine common themes and topics\.

Each operation can be processed in several ways:
+ [Single\-Document Processing](how-single.md)—You call Amazon Comprehend with a single document and receive a synchronous response\. 
+ [Multiple Document Synchronous Processing](how-batch.md)—You call Amazon Comprehend with a collection of up to 25 documents and receive a synchronous response\.
+ [Asynchronous Batch Processing](how-async.md)—You put a collection of documents into an Amazon S3 bucket and start an asynchronous operation to analyze the documents\. The results of the analysis are returned in an S3 bucket\.