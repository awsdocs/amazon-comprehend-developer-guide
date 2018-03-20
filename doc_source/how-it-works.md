# How It Works<a name="how-it-works"></a>

Amazon Comprehend uses a pre\-trained model to examine a document or set of documents to gather insights about the document set\. Amazon Comprehend can examine documents in either English or Spanish\. The model is continuously trained on a large body of text so that there is no need for you to provide training data\. Amazon Comprehend provides the following operations:

+ [DetectDominantLanguage](API_DetectDominantLanguage.md) – to detect the dominant language in a document\. Amazon Comprehend can detect 101 different languages\.

+ [DetectEntities](API_DetectEntities.md) – to detect the entities, such as persons or places, in the document\.

+ [DetectKeyPhrases](API_DetectKeyPhrases.md) – to detect key noun phrases that are most indicative of the content\.

+ [DetectSentiment](API_DetectSentiment.md) – to detect the emotional sentiment, positive, negative, mixed, or neutral, of a document\.

+ [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) – to detect topics in a set of documents\.

All of the operations work on a single document\. You can send up to 25 documents in a single batch using the batch operations\. When you send a batch, Amazon Comprehend returns a list of responses, one for each document that you sent\.

You can use the following batch operations:

+ [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md)

+ [BatchDetectEntities](API_BatchDetectEntities.md)

+ [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md)

+ [BatchDetectSentiment](API_BatchDetectSentiment.md)

**Topic Modeling**  
The `StartTopicsDetectionJob` operation starts an asynchronous operation that processes a set of documents stored in an Amazon S3 bucket to determine the topics in the document set\. Amazon Comprehend trains its topic model on the corpus of documents that you supply, and then assigns documents and topics based on the insights that it discovered\.