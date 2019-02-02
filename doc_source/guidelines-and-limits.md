# Guidelines and Limits<a name="guidelines-and-limits"></a>

Keep in mind the following information when using Amazon Comprehend\.

## Supported Regions<a name="limits-regions"></a>

For a list of AWS Regions where Amazon Comprehend is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend_region) in the *Amazon Web Services General Reference*\.

## Throttling<a name="limits-throttling"></a>

For information about throttling for Amazon Comprehend and to request a limit increase, see [ Amazon Comprehend Limits ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend) in the *Amazon Web Services General Reference*\. 

You may be able to avoid throttling by using the batch operations instead of the single transaction operations\. For more information, see [Multiple Document Operations](#limits-batch)\.

## Overall Limits<a name="limits-all"></a>

All operations except asynchronous operations and topic modeling operations have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 5,000 bytes | 

Amazon Comprehend may store your content to continuously improve the quality of its analysis models\. See the [Amazon Comprehend FAQ](https://aws.amazon.com/comprehend/faqs/) to learn more\. To request that we delete content that may have been stored by Amazon Comprehend, open a case with AWS Support\.

## Multiple Document Operations<a name="limits-batch"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [BatchDetectEntities](API_BatchDetectEntities.md), [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md), and [BatchDetectSentiment](API_BatchDetectSentiment.md) operations have the following limits:


| Description | Limit | 
| --- | --- | 
| Documents per request | 25 | 

If you plan to send more than 20 requests per second, you should consider using the batch operations\. Batch operations enable you to send more documents in each request which may result in higher throughput\. For example, when you use the `DetectDominantLanguage` operation, you can send up to 20 documents per second\. However, if you use the `BatchRequestDominantLanguage` operation, you can send up to 250 documents per second, but processing speed may be lower\. For more information about throttling limits see [ Amazon Comprehend Limits ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend) in the *Amazon Web Services General Reference*\. For more information about using the multiple document APIs, see [Multiple Document Synchronous Processing](how-batch.md)\.

## Asynchronous Operations<a name="limits-asynchronous"></a>

Asynchronous batches started with the [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md), [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md), [StartKeyPhrasesDetectionJob](API_StartKeyPhrasesDetectionJob.md), and [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md) have the following limits:


| Description | Limit | 
| --- | --- | 
| Maximum size \(UTF\-8 characters\) for one document, entity and key phrase detection | 100 KB | 
| Maximum size \(UTF\-8 characters\) for one document, language detection | 1 MB | 
| Maximum size \(UTF\-8 characters\) for one document, sentiment detection | 5 KB | 
| Total size of all files in batch | 5 GB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line | 1,000,000 | 

You should use the asynchronous operations:
+ To analyze more than 25 documents at a time
+ To analyze documents larger than 5,000 bytes for keywords and entities

For more information, see [Asynchronous Batch Processing](how-async.md)\.

## Document Classification<a name="limits-document-classification"></a>

Document classifier training jobs started with the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation and document classification jobs started with the [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) operation have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of labels | 1,000 | 
| Maximum length of labels | 5,000 characters | 
| Total size of all files in request | 5 GB | 
| Maximum file size for one file, one document per file | 100 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line | 1,000,000 | 

## Language Detection<a name="limits-language-detection"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [DetectDominantLanguage](API_DetectDominantLanguage.md) operations and asynchronous jobs started with the [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md) operation have the following limitations:
+ They don't support phonetic language detection\. For example, they will not detect "arigato" as Japanese nor "nihao" as Chinese\.
+ They may have trouble distinguishing close language pairs, such as Indonesian and Malay; or Bosnian, Croatian, and Serbian\.
+ For best results the input text should be at least 20 characters long\.

## Topic Modeling<a name="limits-topic-modeling"></a>

Topic detection jobs created with the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of topics to return | 100 | 
| Total size of all files in request | 5 GB | 
| Maximum file size for one file, one document per file | 100 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line | 1,000,000 | 

For best results, you should include at least 1,000 input documents\.

## Custom Entity Recognition<a name="limits-custom-entity-recognition"></a>

Custom entity recognition jobs started with the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation have the following limits:


**General**  

| Description | Minimum | Maximum | 
| --- | --- | --- | 
| Number of entities per model/custom entity recognizer | \-\- | 1 | 
| Document size \(UTF\-8\) | 1 byte | 5,000 | 
| Number of documents | 2,000 | 120,000 | 
| Document corpus size \(all docs in plain text combined\) | 5 KB | 100 MB | 


**Annotations**  

| Description | Minimum | Maximum | 
| --- | --- | --- | 
| Number of annotations | 1,000 | n/a | 


**Entity Lists**  

| Description | Minimum | Maximum | 
| --- | --- | --- | 
| Number of items in entity list | 1 | 1,000,000 | 
| Length of individual entry \(post\-strip\) in entry list | 1 | 5,000 | 
| Entity list corpus size \(all docs in plain text combined\) | 5 KB | 100 MB | 