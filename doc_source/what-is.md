# What Is Amazon Comprehend?<a name="what-is"></a>

Amazon Comprehend uses natural language processing \(NLP\) to extract insights about the content of documents\. Amazon Comprehend processes any text file in UTF\-8 format, and semi\-structured documents, like PDF and Word documents\. It develops insights by recognizing the entities, key phrases, language, sentiments, and other common elements in a document\. Use Amazon Comprehend to create new products based on understanding the structure of documents\. For example, using Amazon Comprehend you can search social networking feeds for mentions of products or scan an entire document repository for key phrases\.

You work with one or more documents at a time to evaluate their content and gain insights about them\. Some of the insights that Amazon Comprehend develops about a document include:
+ **Entities** – Amazon Comprehend returns a list of entities, such as people, places, and locations, identified in a document\. For more information, see [Detect Entities](how-entities.md)\.
+ **Key phrases** – Amazon Comprehend extracts key phrases that appear in a document\. For example, a document about a basketball game might return the names of the teams, the name of the venue, and the final score\. For more information, see [Detect Key Phrases](how-key-phrases.md)\.
+ **PII** – Amazon Comprehend analyzes documents to detect personal data that could be used to identify an individual, such as an address, bank account number, or phone number\. For more information, see [Detect Personally Identifiable Information \(PII\)](how-pii.md)\.
+ **Language** – Amazon Comprehend identifies the dominant language in a document\. Amazon Comprehend can identify 100 languages\. For more information, see [Detect the Dominant Language](how-languages.md)\.
+ **Sentiment** – Amazon Comprehend determines the emotional sentiment of a document\. Sentiment can be positive, neutral, negative, or mixed\. For more information, see [Determine Sentiment](how-sentiment.md)\. 
+ **Syntax** – Amazon Comprehend parses each word in your document and determines the part of speech for the word\. For example, in the sentence "It is raining today in Seattle," "it" is identified as a pronoun, "raining" is identified as a verb, and "Seattle" is identified as a proper noun\. For more information, see [Analyze Syntax](how-syntax.md)\. 

## Comprehend Custom<a name="how-doc-class"></a>

Customize Comprehend for your specific requirements without the skillset required to build machine learning\-based NLP solutions\. Using automatic machine learning, or AutoML, Comprehend Custom builds customized NLP models on your behalf, using data you already have\.

Custom Classification: Create custom document classifiers to organize your documents into your own categories\. For each classification label, provide a set of documents that best represent that label and train your classifier on it\. Once trained, a classifier can be used on any number of unlabeled document sets\. You can use the console for a code\-free experience or install the latest AWS SDK\. For more information, see [Custom Classification](how-document-classification.md)\.

Custom Entities: Create custom entity types that analyze text for your specific terms and noun\-based phrases\. You can train custom entities to extract terms like policy numbers, or phrases that imply a customer escalation\. To train the model, you provide a list of the entities and a set of documents that contain them\. Once the model is trained, you can submit analysis jobs against it to extract their custom entities\. For more information, see [Custom Entity Recognition](custom-entity-recognition.md)\. 

## Document Clustering \(Topic Modeling\)<a name="how-topics"></a>

You can also use Amazon Comprehend to examine a corpus of documents to organize them based on similar keywords within them\. Document clustering \(topic modeling\) is useful to organize a large corpus of documents into topics or clusters that are similar based on the frequency of words within them\.

Topic modeling is a asynchronous process, you submit a set of documents for processing and then later get the results when processing is complete\. Amazon Comprehend does topic modeling on large document sets, for best results you should include at least 1,000 documents when you submit a topic modeling job\. For more information, see [Topic Modeling](topic-modeling.md)\.

## Examples<a name="how-examples"></a>

The following examples show how you might use the Amazon Comprehend operations in your applications\.

**Example 1: Find documents about a subject**  
Find the documents about a particular subject using Amazon Comprehend topic modeling\. Scan a set of documents to determine the topics discussed, and to find the documents associated with each topic\. You can specify the number of topics that Amazon Comprehend should return from the document set\.

**Example 2: Find out how customers feel about your products**  
If your company publishes a catalog, let Amazon Comprehend tell you what customers think of your products\. Send each customer comment to the `DetectSentiment` operation and it will tell you whether customers feel positive, negative, neutral, or mixed about a product\. 

**Example 3: Discover what matters to your customers**  
Use Amazon Comprehend topic modeling to discover the topics that your customers are talking about on your forums and message boards, then use entity detection to determine the people, places, and things that they associate with the topic\. Finally, use sentiment analysis to determine how your customers feel about a topic\.

## Benefits<a name="how-benefits"></a>

Some of the benefits of using Amazon Comprehend include:
+ **Integrate powerful natural language processing into your apps**—Amazon Comprehend removes the complexity of building text analysis capabilities into your applications by making powerful and accurate natural language processing available with a simple API\. You don't need textual analysis expertise to take advantage of the insights that Amazon Comprehend produces\.
+ **Deep learning based natural language processing**—Amazon Comprehend uses deep learning technology to accurately analyze text\. Our models are constantly trained with new data across multiple domains to improve accuracy\.
+ **Scalable natural language processing**—Amazon Comprehend enables you to analyze millions of documents so that you can discover the insights that they contain\.
+ **Integrate with other AWS services**—Amazon Comprehend is designed to work seamlessly with other AWS services like Amazon S3, AWS KMS, and AWS Lambda\. Store your documents in Amazon S3, or analyze real\-time data with Kinesis Data Firehose\. Support for AWS Identity and Access Management \(IAM\) makes it easy to securely control access to Amazon Comprehend operations\. Using IAM, you can create and manage AWS users and groups to grant the appropriate access to your developers and end users\.
+ **Encryption of output results and volume data **—Amazon S3 already enables you to encrypt your input documents, and Amazon Comprehend extends this even farther\. By using your own KMS key, you can not only encrypt the output results of your job, but also the data on the storage volume attached to the compute instance that processes the analysis job\. The result is significantly enhanced security\.
+ **Low cost**—With Amazon Comprehend, you only pay for the documents that you analyze\. There are no minimum fees or upfront commitments\. 

## Are You a First\-time User of Amazon Comprehend?<a name="first-time-user"></a>

If you are a first\-time user of Amazon Comprehend, we recommend that you read the following sections in order:

1. **[How It Works](how-it-works.md)** – This section introduces Amazon Comprehend concepts\. 

1. **[Getting Started with Amazon Comprehend](getting-started.md)** – In this section, you set up your account and test Amazon Comprehend\. 

1. ** [API Reference](API_Reference.md) ** – In this section you'll find reference documentation for Amazon Comprehend operations\.