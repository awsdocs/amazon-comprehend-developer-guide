# Topic Modeling<a name="topic-modeling"></a>

You can use Amazon Comprehend to examine the content of a collection of documents to determine common themes\. For example, you can give Amazon Comprehend a collection of news articles, and it will determine the subjects, such as sports, politics, or entertainment\. The text in the documents doesn't need to be annotated\. 

Amazon Comprehend uses a [Latent Dirichlet Allocation](http://www.jmlr.org/papers/volume3/blei03a/blei03a.pdf)\-based learning model to determine the topics in a set of documents\. It examines each document to determine the context and meaning of a word\. The set of words that frequently belong to the same context across the entire document set make up a topic\.

A word is associated to a topic in a document based on how prevalent that topic is in a document and how much affinity the topic has to the word\. The same word can be associated with different topics in different documents based on the topic distribution in a particular document\. 

For example, the word "glucose" in an article that talks predominantly about sports can be assigned to the topic "sports," while the same word in an article about "medicine" will be assigned to the topic "medicine\."

Each word associated with a topic is given a weight that indicates how much the word helps define the topic\. The weight is an indication of how many times the word occurs in the topic compared to other words in the topic, across the entire document set\.

For the most accurate results you should provide Amazon Comprehend with the largest possible corpus to work with\. For best results:
+ You should use at least 1,000 documents in each topic modeling job\.
+ Each document should be at least 3 sentences long\.
+ If a document consists of mostly numeric data, you should remove it from the corpus\.

Topic modeling is an asynchronous process\. You submit your list of documents to Amazon Comprehend from an Amazon S3 bucket using the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation\. The response is sent to an Amazon S3 bucket\. You can configure both the input and output buckets\. Get a list of the topic modeling jobs that you have submitted using the [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md) operation and view information about a job using the [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md) operation\. Content delivered to Amazon S3 buckets might contain customer content\. For more information about removing sensitive data, see [How Do I Empty an S3 Bucket?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/empty-bucket.html) or [How Do I Delete an S3 Bucket?](https://docs.aws.amazon.com/AmazonS3/latest/user-guide/delete-bucket.html)\.

Documents must be in UTF\-8 formatted text files\. You can submit your documents two ways\. The following table shows the options\.


| Format | Description | 
| --- | --- | 
| One document per file | Each file contains one input document\. This is best for collections of large documents\. | 
| One document per line | The input is a single file\. Each line in the file is considered a document\. This is best for short documents, such as social media postings\. Each line must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. The Unicode line separator \(u\+2028\) can't be used to end a line\. | 

For more information, see the [InputDataConfig](API_InputDataConfig.md) data type\.

After Amazon Comprehend processes your document collection, it returns a compressed archive containing two files, `topic-terms.csv` and `doc-topics.csv`\. For more information about the output file, see [OutputDataConfig](API_OutputDataConfig.md)\. 

The first output file, `topic-terms.csv`, is a list of topics in the collection\. For each topic, the list includes, by default, the top terms by topic according to their weight\. For example, if you give Amazon Comprehend a collection of newspaper articles, it might return the following to describe the first two topics in the collection:


| Topic | Term | Weight | 
| --- | --- | --- | 
| 000 | team | 0\.118533 | 
| 000 | game | 0\.106072 | 
| 000 | player | 0\.031625 | 
| 000 | season | 0\.023633 | 
| 000 | play | 0\.021118 | 
| 000 | yard | 0\.024454 | 
| 000 | coach | 0\.016012 | 
| 000 | games | 0\.016191 | 
| 000 | football | 0\.015049 | 
| 000 | quarterback | 0\.014239 | 
| 001 | cup | 0\.205236 | 
| 001 | food | 0\.040686 | 
| 001 | minutes | 0\.036062 | 
| 001 | add | 0\.029697 | 
| 001 | tablespoon | 0\.028789 | 
| 001 | oil | 0\.021254 | 
| 001 | pepper | 0\.022205 | 
| 001 | teaspoon | 0\.020040 | 
| 001 | wine | 0\.016588 | 
| 001 | sugar | 0\.015101 | 

The weights represent a probability distribution over the words in a given topic\. Since Amazon Comprehend returns only the top 10 words for each topic the weights won't sum to 1\.0\. In the rare cases where there are less than 10 words in a topic, the weights will sum to 1\.0\.

The words are sorted by their discriminative power by looking at their occurrence across all topics\. Typically this is the same as their weight, but in some cases, such as the words "play" and "yard" in the table, this results in an order that is not the same as the weight\.

You can specify the number of topics to return\. For example, if you ask Amazon Comprehend to return 25 topics, it returns the 25 most prominent topics in the collection\. Amazon Comprehend can detect up to 100 topics in a collection\. Choose the number of topics based on your knowledge of the domain\. It may take some experimentation to arrive at the correct number\. 

The second file, `doc-topics.csv`, lists the documents associated with a topic and the proportion of the document that is concerned with the topic\. If you specified `ONE_DOC_PER_FILE` the document is identified by the file name\. If you specified `ONE_DOC_PER_LINE` the document is identified by the file name and the 0\-indexed line number within the file\. For example, Amazon Comprehend might return the following for a collection of documents submitted with one document per file:


| Document | Topic | Proportion | 
| --- | --- | --- | 
| sample\-doc1 | 000 | 0\.999330137 | 
| sample\-doc2 | 000 | 0\.998532187 | 
| sample\-doc3 | 000 | 0\.998384574 | 
| \.\.\. |   |   | 
| sample\-docN | 000 | 3\.57E\-04 | 

Amazon Comprehend utilizes information from the *Lemmatization Lists Dataset by MBM*, which is made available [here](https://github.com/michmech/lemmatization-lists) under the [Open Database License \(ODbL\) v1\.0](https://opendatacommons.org/licenses/odbl/1-0/)\.