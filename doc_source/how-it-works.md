# How It Works<a name="how-it-works"></a>

Amazon Comprehend uses a pre\-trained model to examine and analyze a document or set of documents to gather insights about it\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. 

Amazon Comprehend can examine and analyze documents in a variety of languages, depending on the specific feature\. For more information, see [Amazon Comprehend supported languages](https://docs.aws.amazon.com/comprehend/latest/dg/supported-languages.html#supported-languages-1)\. 

Additionally, Amazon Comprehend's [Detect the Dominant Language](how-languages.md) operation can examine documents and determine the dominant language out of a far wider variety of different languages\. For more information, see [Languages Supported in Amazon Comprehend](supported-languages.md)\.

With Amazon Comprehend, you can perform the following on your documents:
+ [Detect the Dominant Language](how-languages.md) – Examine text to determine the dominant language\.
+ [Detect Entities](how-entities.md) – Detect textual references to the names of people, places, and items as well as references to dates and quantities\.
+ [Detect Key Phrases](how-key-phrases.md) – Find key phrases such as "good morning" in a document or set of documents\.
+ [Detect Personally Identifiable Information \(PII\)](how-pii.md) – Analyze documents to detect personal data that could be used to identify an individual, such as an address, bank account number, or phone number\.
+ [Determine Sentiment](how-sentiment.md) – Amazon Comprehend determines the dominant sentiment of a document\. Sentiment can be positive, neutral, negative, or mixed\. 
+ [Analyze Targeted Sentiment](how-targeted-sentiment.md) – Amazon Comprehend determines the sentiment of specific entities mentioned in a document\. The sentiment of each mention can be positive, neutral, negative, or mixed\. 
+ [Analyze Syntax](how-syntax.md) – Parse the words in your text and show the speech syntax for each word and enable you to understand the content of the document\.
+ [Topic Modeling](topic-modeling.md) – Search the content of documents to determine common themes and topics\.



Each operation can be processed in several ways:
+ [Single\-Document Processing](how-single.md) – You call Amazon Comprehend with a single document and receive a synchronous response\. 
+ [Multiple Document Synchronous Processing](how-batch.md) – You call Amazon Comprehend with a collection of up to 25 documents and receive a synchronous response\.
+ [Asynchronous Batch Processing](how-async.md) – You put a collection of documents into an Amazon S3 bucket and start an asynchronous operation to analyze the documents\. The results of the analysis are returned in an S3 bucket\.

Each operation can be encrypted both during communication and processing\.

By using the integrated AWS KMS encryption, you maintain control over who can access to your encrypted data\. 

You can optionally provide a custom KMS key when you create your analysis job and your data will be encrypted on the storage volume attached to the ML compute instance processing the job\. You can also provide a key to encrypt your output results as it's sent to the S3 bucket\. If you have set up encryption on the S3 bucket that holds your input documents, this can provide you with end\-to\-end security\. 

For more information, see [KMS Encryption in Amazon Comprehend](kms-in-comprehend.md)\.

