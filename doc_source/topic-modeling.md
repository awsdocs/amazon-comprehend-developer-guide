# Topic Modeling<a name="topic-modeling"></a>

You can use Amazon Comprehend to examine the content of a collection of documents to determine common themes\. For example, you can give Amazon Comprehend a collection of news articles, and it will determine the subjects, such as sports, politics, or entertainment\. The text in the documents doesn't need to be annotated\. 

Amazon Comprehend uses an LDA\-based learning model to determine the topics in a set of documents\. It examines each document to determine the context and meaning of a word\. The set of words that frequently belong to the same context across the entire document set make up a topic\.

A word is associated to a topic in a document based on how prevalent that topic is in a document and how much affinity the topic has to the word\. The same word can be associated with different topics in different documents based on the topic distribution in a particular document\. 

For example, the word "glucose" in an article that talks predominantly about sports can be assigned to the topic "sports," while the same word in an article about "medicine" will be assigned to the topic "medicine\."

Each word associated with a topic is given a weight that indicates how much the word helps define the topic\. The weight is an indication of how many times the word occurs in the topic compared to other words in the topic, across the entire document set\.

For the most accurate results you should provide Amazon Comprehend with the largest possible corpus to work with\. For best results, you should use at least 1,000 documents in each topic modeling job\.

Topic modeling is an asynchronous process\. You submit your list of documents to Amazon Comprehend from an Amazon S3 bucket using the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation\. The response is sent to an Amazon S3 bucket\. You can configure both the input and output buckets\. Get a list of the topic modeling jobs that you have submitted using the [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) operation and view information about a job using the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation\.

You can submit your documents two ways\. The following table shows the options\.


| Format | Description | 
| --- | --- | 
| One document per file | Each file contains one input document\. All files names must begin with a common prefix\. This is best for collections of large documents\. | 
| One document per line | The input is a single file\. Each line in the file is considered a document\. This is best for short documents, such as social media postings\. | 

For more information, see the [InputDataConfig](API_InputDataConfig.md) data type\.

After Amazon Comprehend processes your document collection, it returns a compressed archive containing two files, `topic-terms.csv` and `doc-topics.csv`\. For more information about the output file, see [OutputDataConfig](API_OutputDataConfig.md)\. 

The first output file, `topic-terms.csv`, is a list of topics in the collection\. For each topic, the list includes, by default, the 10 terms most closely associated with a topic\. For example, if you give Amazon Comprehend a collection of newspaper articles, it might return the following to describe the first two topics in the collection:


| Topic | Term | Weight | 
| --- | --- | --- | 
| 000 | team | 26347\.04884 | 
| 000 | game | 18297\.04884 | 
| 000 | player | 15169\.04884 | 
| 000 | season | 14524\.04884 | 
| 000 | play | 12563\.04884 | 
| 000 | yard | 12298\.04884 | 
| 000 | coach | 10677\.04884 | 
| 000 | games | 10579\.04884 | 
| 000 | football | 10159\.04884 | 
| 000 | quarterback | 8628\.048837 | 
| 001 | cup | 12431\.04884 | 
| 001 | food | 9474\.048837 | 
| 001 | minutes | 8277\.048837 | 
| 001 | add | 7572\.048837 | 
| 001 | tablespoon | 6589\.048837 | 
| 001 | oil | 6202\.048837 | 
| 001 | pepper | 5362\.048837 | 
| 001 | teaspoon | 5341\.048837 | 
| 001 | wine | 5116\.048837 | 
| 001 | sugar | 5023\.048837 | 

You can specify the number of topics to return\. For example, if you ask Amazon Comprehend to return 25 topics, it returns the 25 most prominent topics in the collection\. Choose the number of topics based on your knowledge of the domain\. It may take some experimentation to arrive at the correct number\. 

The second file, `doc-topics.csv`, lists the documents associated with a topic and the proportion of the document that is concerned with the topic\. For example, Amazon Comprehend might return the following for a collection of documents:


| Document | Topic | Proportion | 
| --- | --- | --- | 
| sample\-doc1 | 000 | 0\.999330137 | 
| sample\-doc2 | 000 | 0\.998532187 | 
| sample\-doc3 | 000 | 0\.998384574 | 
| \.\.\. |   |   | 
| sample\-docN | 000 | 3\.57E\-04 | 

Amazon Comprehend utilizes information from the *Lemmatization Lists Dataset by MBM*, which is made available [here](http://www.lexiconista.com/datasets/lemmatization/) under the [Open Database License \(ODbL\) v1\.0](https://opendatacommons.org/licenses/odbl/1-0/)\.

## Role\-based Data Access<a name="detect-topics-role-auth"></a>

To use the Amazon Comprehend topic modeling operations, you must grant Amazon Comprehend access to the Amazon S3 bucket that contains your document collection\. For more information, see [Role\-Based Permissions Required for Topic Detection](access-control-managing-permissions.md#auth-role-permissions)\.