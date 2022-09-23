# What is Amazon Comprehend?<a name="what-is"></a>

Amazon Comprehend uses natural language processing \(NLP\) to extract insights about the content of documents\. It develops insights by recognizing the entities, key phrases, language, sentiments, and other common elements in a document\. Use Amazon Comprehend to create new products based on understanding the structure of documents\. For example, using Amazon Comprehend you can search social networking feeds for mentions of products or scan an entire document repository for key phrases\.

You can access Amazon Comprehend document analysis capabilities using the Amazon Comprehend console or using the Amazon Comprehend APIs\. You can run real\-time analysis for small workloads or you can start asynchronous analysis jobs for large document sets\. You can use the pre\-trained models that Amazon Comprehend provides, or you can train your own custom models for classification and entity recognition\.

All of the Amazon Comprehend features can analyze UTF\-8 text documents as the input files\. In addition, custom entity recognition can analyze image files, PDF files, and Word files\. 

Amazon Comprehend can examine and analyze documents in a variety of languages, depending on the specific feature\. For more information, see [Languages supported in Amazon Comprehend](supported-languages.md)\. Amazon Comprehend's [Dominant language](how-languages.md) capability can examine documents and determine the dominant language for a far wider selection of languages\.

**Topics**
+ [Amazon Comprehend insights](#what-is-insights)
+ [Amazon Comprehend Custom](#how-doc-class)
+ [Document clustering \(topic modeling\)](#how-topics)
+ [Examples](#how-examples)
+ [Benefits](#how-benefits)
+ [Amazon Comprehend pricing](#what-pricing)
+ [Are you a first\-time user of Amazon Comprehend?](#first-time-user)

## Amazon Comprehend insights<a name="what-is-insights"></a>

Amazon Comprehend uses a pre\-trained model to examine and analyze a document or set of documents to gather insights about it\. This model is continuously trained on a large body of text so that there is no need for you to provide training data\. 

Amazon Comprehend gathers the following types of insights:
+ **Entities** – References to the names of people, places, items, and locations contained in a document\. 
+ **Key phrases** – Phrases that appear in a document\. For example, a document about a basketball game might return the names of the teams, the name of the venue, and the final score\. 
+ **Personally Identifiable Information \(PII\)** – Personal data that can identify an individual, such as an address, bank account number, or phone number\. 
+ **Language** – The dominant language of a document\. 
+ **Sentiment** – The dominant sentiment of a document, which can be positive, neutral, negative, or mixed\. 
+ **Targeted sentiment** – The sentiments associated with specific entities in a document\. The sentiment for each entity occurrence can be positive, negative, neutral or mixed\. 
+ **Syntax** – The parts of speech for each word in the document\. 

For more information, see [Insights](concepts-insights.md)\.

## Amazon Comprehend Custom<a name="how-doc-class"></a>

You can customize Amazon Comprehend for your specific requirements without the skillset required to build machine learning\-based NLP solutions\. Using automatic machine learning, or AutoML, Amazon Comprehend Custom builds customized NLP models on your behalf, using data you already have\.

**Custom classification** – Create custom classification models \(classifiers\) to organize your documents into your own categories\. 

**Custom entity recognition** – Create custom entity recognition models \(recognizers\) that can analyze text for your specific terms and noun\-based phrases\. 

For more information, see [Amazon Comprehend Custom](concepts-custom.md)\. 

## Document clustering \(topic modeling\)<a name="how-topics"></a>

You can also use Amazon Comprehend to examine a corpus of documents to organize them based on similar keywords within them\. Document clustering \(topic modeling\) is useful to organize a large corpus of documents into topics or clusters that are similar based on word frequency\. For more information, see [Topic modeling](topic-modeling.md)\.

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
+ **Integrate powerful natural language processing into your apps** – Amazon Comprehend removes the complexity of building text analysis capabilities into your applications by making powerful and accurate natural language processing available with a simple API\. You don't need textual analysis expertise to take advantage of the insights that Amazon Comprehend produces\.
+ **Deep learning based natural language processing** – Amazon Comprehend uses deep learning technology to accurately analyze text\. Our models are constantly trained with new data across multiple domains to improve accuracy\.
+ **Scalable natural language processing** – Amazon Comprehend enables you to analyze millions of documents so that you can discover the insights that they contain\.
+ **Integrate with other AWS services** – Amazon Comprehend is designed to work seamlessly with other AWS services like Amazon S3, AWS KMS, and AWS Lambda\. Store your documents in Amazon S3, or analyze real\-time data with Kinesis Data Firehose\. Support for AWS Identity and Access Management \(IAM\) makes it easy to securely control access to Amazon Comprehend operations\. Using IAM, you can create and manage AWS users and groups to grant the appropriate access to your developers and end users\.
+ **Encryption of output results and volume data ** – Amazon S3 already enables you to encrypt your input documents, and Amazon Comprehend extends this even farther\. By using your own KMS key, you can not only encrypt the output results of your job, but also the data on the storage volume attached to the compute instance that processes the analysis job\. The result is significantly enhanced security\.
+ **Low cost** – With Amazon Comprehend, there are no minimum fees or upfront commitments\. You pay for the documents that you analyze and custom models that you train\. 

## Amazon Comprehend pricing<a name="what-pricing"></a>

There is a usage charge for running real\-time or asynchronous analysis jobs\. You pay to train custom models, and you pay for custom model management\. For real\-time requests using custom models, you pay for the endpoint from the time that you start your endpoint until you delete the endpoint\.

For the rates and additional detailed information, see [http://aws.amazon.com/comprehend/pricing](http://aws.amazon.com/comprehend/pricing)\.

## Are you a first\-time user of Amazon Comprehend?<a name="first-time-user"></a>

If you are a first\-time user of Amazon Comprehend, we recommend that you read the following sections in order:

1. **[How it works](how-it-works.md)** – This section introduces Amazon Comprehend concepts\. 

1. **[Setting up](setting-up.md)** – In this section, you create an IAM user and set up the AWS CLI\. 

1. **[Getting started with Amazon Comprehend](getting-started.md)** – In this section, you run a Amazon Comprehend analysis job\. 

1. **[Tutorial: Analyzing insights from customer reviews with Amazon Comprehend](tutorial-reviews.md)** – In this section, you perform sentiment and entities analysis and visualize the results\.

1. ** [Amazon Comprehend API Reference](https://docs.aws.amazon.com/api-ref)\. **– Reference documentation for Amazon Comprehend operations\.

AWS provides the following resources for learning about the Amazon Comprehend service:
+ The [AWS Machine Learning Blog](http://aws.amazon.com/blogs/machine-learning/ ) includes useful articles about Amazon Comprehend\.
+ [Amazon Comprehend Resources](http://aws.amazon.com/comprehend/resources/) provides useful videos and tutorials about Amazon Comprehend\.