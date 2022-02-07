# Guidelines and Quotas<a name="guidelines-and-limits"></a>

Many of the Amazon Comprehend quotas shown here can be increased if needed for your applications\. For information about service quotas and to request a quota increase, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

Remember the following information when using Amazon Comprehend\.

## Supported Regions<a name="limits-regions"></a>

For a list of AWS Regions where Amazon Comprehend is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend_region) in the *Amazon Web Services General Reference*\.

## Overall Quotas<a name="limits-all"></a>

All operations except asynchronous operations and topic modeling operations have the following quotas:


| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 5,000 bytes | 

Synchronous requests to label documents with PII using the [ContainsPiiEntities](API_ContainsPiiEntities.md) operation have the following quotas:


| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 50,000 bytes | 

Amazon Comprehend may store your content to continuously improve the quality of its analysis models\. See the [Amazon Comprehend FAQ](https://aws.amazon.com/comprehend/faqs/) to learn more\. 

## Throttling When Using Single Transactions<a name="limits-throttling"></a>

You may be able to avoid throttling by using the batch operations instead of the single transaction operations\. For more information, see [Multiple Document Operations](#limits-batch)\.

## Multiple Document Operations<a name="limits-batch"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [BatchDetectEntities](API_BatchDetectEntities.md), [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md), and [BatchDetectSentiment](API_BatchDetectSentiment.md) operations have the following quotas:


| Description | Quota/Guideline | 
| --- | --- | 
| Documents per request | 25 | 

If you plan to send more than 20 requests per second, you should consider using the batch operations\. Batch operations enable you to send more documents in each request which may result in higher throughput\. For example, when you use the `DetectDominantLanguage` operation, you can send up to 20 documents per second\. However, if you use the `BatchRequestDominantLanguage` operation, you can send up to 250 documents per second, but processing speed may be lower\. For more information about throttling quotas see [ Amazon Comprehend Quotas ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend) in the *Amazon Web Services General Reference*\. For more information about using the multiple document APIs, see [Multiple Document Synchronous Processing](how-batch.md)\.

## Asynchronous Operations<a name="limits-asynchronous"></a>

Asynchronous batch jobs are run with the [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md), [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md), [StartKeyPhrasesDetectionJob](API_StartKeyPhrasesDetectionJob.md), [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md), and [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md) operations\. These jobs have the following limits:


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum size of each document in jobs that detect entities, key phrases, PII, and languages | 1 MB | 
| Maximum size of each document in jobs that detect sentiment | 5 KB | 
| Total size of all files in batch | 5 GB | 
| Maximum number of files, one document per file | 1,000,000 | 

You should use the asynchronous operations:
+ To analyze more than 25 documents at a time
+ To analyze documents larger than 5,000 bytes for keywords and entities

For more information, see [Asynchronous Batch Processing](how-async.md)\.

## Document Classification<a name="limits-document-classification"></a>

Document classifier training jobs started with the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation, asynchronous document classification jobs started with the [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) , and synchronous document classification requests started with the [ClassifyDocument](API_ClassifyDocument.md) operation have the following limits: 


**General**  

| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of classes \(multi\-class mode\) | 1,000 | 
| Maximum number of classes \(multi\-label mode\) | 100 | 
| Maximum length of class name | 5,000 characters | 
| Minimum number of training documents per class \(multi\-class mode\) | 50 | 
| Minimum number of training documents per class, \(multi\-label mode\) | 10 | 
| Total size of all files in training job | 5 GB | 
| Total size of all files in asynchronous job | 5 GB | 
| Maximum file size for one file, one document per file | 10 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 1,000,000 | 
| Maximum number of documents per synchronous request | 1 | 
| Maximum number of augmented manifest files for training a custom classifier | 5 | 
| Maximum number of attribute names for each augmented manifest file | 5 | 
| Maximum length of attribute name | 63 characters | 


**Real\-time analysis**  

| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of inference units per account | 100 | 
| Maximum number of inference units per endpoint | 10 | 
| Maximum throughput per inference unit \(characters\) | 100/second | 
| Maximum throughput per inference unit \(documents\) | 2/second | 

## Language Detection<a name="limits-language-detection"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [DetectDominantLanguage](API_DetectDominantLanguage.md) operations and asynchronous jobs started with the [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md) operation have the following limitations:
+ They don't support phonetic language detection\. For example, they will not detect "arigato" as Japanese nor "nihao" as Chinese\.
+ They may have trouble distinguishing close language pairs, such as Indonesian and Malay; or Bosnian, Croatian, and Serbian\.
+ For best results the input text should be at least 20 characters long\.

## Events<a name="limits-events"></a>

Events detection jobs created with the [StartEventsDetectionJob](API_StartEventsDetectionJob.md) operation have the following limits:


| Description | Quotas | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Total size of all files in a job | 50 MB | 
| Maximum size of each document in a job | 10 KB | 
| Maximum number of files, one document per file | 5,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 5,000 | 

## Topic Modeling<a name="limits-topic-modeling"></a>

Topic detection jobs created with the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation have the following limits:


| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of topics to return | 100 | 
| Maximum total size of all files in request | 5 GB | 
| Minimum total size of all files in request | 500 bytes | 
| Maximum file size for one file, one document per file | 100 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 1,000,000 | 

For best results, you should include at least 1,000 input documents\.

## Entity Recognition<a name="limits-custom-entity-recognition"></a>

Entity recognizer training jobs started with the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation, asynchronous entity recognition jobs started with the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation, and synchronous entity recognition requests started with the [DetectEntities](API_DetectEntities.md) operation have the following limits:


**Plain text entity recognition \- training \(CreateEntityRecognizer\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1 \- 25 | 
| Document size \(UTF\-8\) | 1 \- 5,000 byte | 
| Number of documents | 250 \- 120,000 | 
| Document corpus size \(all docs in plain text combined\) | 5 KB \- 100MB | 
| Minimum number of annotations per entity | 100 | 
| Number of items in entity list | 1 \- 1 million | 
| Length of individual entry \(post\-strip\) in entry list | 1 \- 5,000 | 
| Entity list corpus size \(all docs in plain text combined\) | 5KB \- 100 MB | 


**PDF or Word text entity recognition \- training \(CreateEntityRecognizer\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1 \- 25 | 
| Maximum annotation file size \(UTF\-8 JSON\) | 5 MB | 
| Number of documents | 250 \- 10,000 | 
| Document corpus size \(all docs in plain text combined\) | 5 KB \- 1 GB | 
| Minimum number of annotations per entity | 100 | 


**Augmented manifest files**  

| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of augmented manifest files for training a custom entity recognizer | 5 | 
| Maximum number of attribute names for each augmented manifest file | 5 | 
| Maximum length of attribute name | 63 characters | 


**Plain text entity recognition \- inference \(StartEntitiesDetectionJob\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(UTF\-8\) | 1 byte \- 1 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 1,000,000 | 
| Document corpus size \(all docs in plain text combined\) | 1 byte \- 5 GB | 


**PDF or Word text entity recognition \- inference \(StartEntitiesDetectionJob\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(PDF\) | 1 byte \- 50 MB | 
| Document size \(Docx\) | 1 byte \- 5 MB | 
| Document size \(UTF\-8\) | 1 byte \- 1 MB | 
| Maximum number of files, one document per file \(one document per line not allowed for PDF or Word documents\) | 500 | 
| Maximum number of pages for single PDF or Docx file | 100 | 
| Document corpus size \(all docs in plain text combined\) | 1 byte \- 5 GB | 


**Real\-time analysis**  

| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of inference units per account | 100 | 
| Maximum number of inference units per endpoint | 10 | 
| Maximum throughput per inference unit \(characters\) | 100/second | 
| Maximum throughput per inference unit \(documents\) | 2/second | 
| Maximum number of documents per synchronous request | 1 | 