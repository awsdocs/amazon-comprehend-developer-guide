# Guidelines and quotas<a name="guidelines-and-limits"></a>

Many of the Amazon Comprehend quotas shown here can be increased if needed for your applications\. For information about service quotas and to request a quota increase, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

Remember the following information when using Amazon Comprehend\.

**Topics**
+ [Supported Regions](#limits-regions)
+ [Overall Quotas](#limits-all)
+ [Throttling for single transactions](#limits-throttling)
+ [Multiple document operations](#limits-batch)
+ [Concurrent active asynchronous jobs](#limits-active-jobs)
+ [Asynchronous jobs](#limits-asynchronous)
+ [Targeted sentiment](#limits-targeted-sentiment)
+ [Document classification](#limits-document-classification)
+ [Language detection](#limits-language-detection)
+ [Events](#limits-events)
+ [Topic modeling](#limits-topic-modeling)
+ [Entity recognition](#limits-custom-entity-recognition)

## Supported Regions<a name="limits-regions"></a>

For a list of AWS Regions where Amazon Comprehend is available, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend_region) in the *Amazon Web Services General Reference*\.

## Overall Quotas<a name="limits-all"></a>

All single\-document synchronous operations except sentiment analysis, targeted sentiment analysis, and syntax analysis have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum document size  | 100 KB | 

The maximum document size for sentiment analysis, targeted sentiment analysis, syntax analysis, and the batch synchronous operations is 5 KB\.

**Note**  
Amazon Comprehend performs real\-time sentiment analysis on the first 500 characters of the input text and ignores any additional text in the input\.

Amazon Comprehend may store your content to continuously improve the quality of its analysis models\. See the [Amazon Comprehend FAQ](https://aws.amazon.com/comprehend/faqs/) to learn more\. 

## Throttling for single transactions<a name="limits-throttling"></a>

You may be able to avoid throttling by using the batch operations instead of the single transaction operations\. For more information, see [Multiple document operations](#limits-batch)\.

## Multiple document operations<a name="limits-batch"></a>

The [BatchDetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectDominantLanguage.html), [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html), [BatchDetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectKeyPhrases.html), and [BatchDetectSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectSentiment.html) operations have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Documents per request | 25 | 

If you plan to send more than 20 requests per second, you should consider using the batch operations\. With batch operations, you send more documents in each request, which may result in higher throughput\. For example, when you use the `DetectDominantLanguage` operation, you can send up to 20 documents per second\. However, if you use the `BatchRequestDominantLanguage` operation, you can send up to 250 documents per second, but processing speed may be lower\. For more information about throttling quotas, see [ Amazon Comprehend Quotas ](https://docs.aws.amazon.com/general/latest/gr/comprehend.html) in the *Amazon Web Services General Reference*\. For more information about using the multiple document API operations, see [Multiple document synchronous processing](concepts-processing-modes.md#how-batch)\.

## Concurrent active asynchronous jobs<a name="limits-active-jobs"></a>

You create new analysis jobs using the Amazon Comprehend console or one of the `API_Start*` operations\. Each account can have up to 10 concurrent active jobs of a given job type\. 


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of concurrent active jobs per job type | 10 | 

## Asynchronous jobs<a name="limits-asynchronous"></a>

Asynchronous analysis jobs that you run using one of the `API_Start*` operations have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum size of each document in jobs that detect entities, key phrases, PII, and languages | 1 MB | 
| Maximum size of each document in jobs that detect sentiment | 5 KB | 
| Total size of all files in batch | 5 GB | 
| Maximum number of files, one document per file | 1,000,000 | 

You should use the asynchronous operations:
+ To analyze more than 25 documents at a time
+ To analyze documents larger than 5,000 bytes for keywords and entities

For more information, see [Asynchronous batch processing](concepts-processing-modes.md#how-async)\.

## Targeted sentiment<a name="limits-targeted-sentiment"></a>

Targeted sentiment supports only asynchronous analysis jobs\. Jobs created with the [StartTargetedSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartTargetedSentimentDetectionJob.html) operation have the following quotas\.


**Targeted sentiment detection \- inference \(StartTargetedSentimentDetectionJob\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Supported document formats | UTF\-8 | 
| Maximum size of each document in a job | 10 KB | 
| Maximum size of all documents in a job | 300 MB | 
| Maximum number of files, one document per file | 30,000 | 
| Maximum number of lines, one document per line \(for all files in a request\) | 30,000 | 

## Document classification<a name="limits-document-classification"></a>

Document classifier training jobs started with the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) operation, asynchronous document classification jobs started with the [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html), and synchronous document classification requests started with the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) operation have the following quotas\. 


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

## Language detection<a name="limits-language-detection"></a>

The [BatchDetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectDominantLanguage.html), [DetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectDominantLanguage.html) operations and asynchronous jobs started with the [StartDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDominantLanguageDetectionJob.html) operation have the following limitations:
+ They don't support phonetic language detection\. For example, they will not detect "arigato" as Japanese nor "nihao" as Chinese\.
+ They may have trouble distinguishing close language pairs, such as Indonesian and Malay; or Bosnian, Croatian, and Serbian\.
+ For best results the input text should be at least 20 characters long\.

## Events<a name="limits-events"></a>

Events detection jobs created with the [StartEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEventsDetectionJob.html) operation have the following quotas\.


| Description | Quotas | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Total size of all files in a job | 50 MB | 
| Maximum size of each document in a job | 10 KB | 
| Maximum number of files, one document per file | 5,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 5,000 | 

## Topic modeling<a name="limits-topic-modeling"></a>

Topic detection jobs created with the [StartTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartTopicsDetectionJob.html) operation have the following quotas\.


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

## Entity recognition<a name="limits-custom-entity-recognition"></a>

Entity recognizer training jobs started with the [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEntityRecognizer.html) operation, asynchronous entity recognition jobs started with the [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEntitiesDetectionJob.html) operation, and synchronous entity recognition requests started with the [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) operation have the following quotas\.


**Plain text entity recognition \- training \(CreateEntityRecognizer\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1–25 | 
| Document size \(UTF\-8\) | 1–5,000 byte | 
| Number of documents \(see [Plain\-text annotations](cer-annotation.md#prep-training-data-ann)\) | 3–120,000 | 
| Document corpus size \(all docs in plaintext combined\) | 5 KB \- 100 MB | 
| Minimum number of annotations per entity | 25 | 
| Number of items in entity list | 1–1 million | 
| Length of individual entry \(post\-strip\) in entry list | 1–5,000 | 
| Entity list corpus size \(all docs in plaintext combined\) | 5 KB –100 MB | 


**PDF or Word text entity recognition \- training \(CreateEntityRecognizer\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1–25 | 
| Maximum annotation file size \(UTF\-8 JSON\) | 5 MB | 
| Number of documents | 250–10,000 | 
| Document corpus size \(all docs in plaintext combined\) | 5 KB–1 GB | 
| Minimum number of annotations per entity | 100 | 


**Augmented manifest files**  

| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of augmented manifest files for training a custom entity recognizer | 5 | 
| Maximum number of attribute names for each augmented manifest file | 5 | 
| Maximum length of attribute name | 63 characters | 


**Entity recognition for plaintext files \- inference \(StartEntitiesDetectionJob\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(UTF\-8\) | 1 byte–1 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 1,000,000 | 
| Document corpus size \(all docs in plaintext combined\) | 1 byte–5 GB | 


**Entity recognition for image, PDF, or Word files \- inference \(StartEntitiesDetectionJob\)**  

| Description | Quota/Guideline | 
| --- | --- | 
| Image size \(JPG or PNG\) | 1 byte–10 MB | 
| Image size \(TIFF\) | 1 byte–10 MB\. Maximum one page\. | 
| Document size \(PDF\) | 1 byte–50 MB | 
| Document size \(Docx\) | 1 byte–5 MB | 
| Document size \(UTF\-8\) | 1 byte–1 MB | 
| Maximum number of files, one document per file \(one document per line not allowed for image files or PDF/Word documents\) | 500 | 
| Maximum number of pages for a PDF or Docx file | 100 | 
| Document corpus size after text extraction \(plaintext, all files combined\) | 1 byte–5 GB | 

For more information about limits for images, see [Hard Limits in Amazon Textract](https://docs.aws.amazon.com/textract/latest/dg/limits.html) 


**Real\-time analysis**  

| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of inference units per account | 100 | 
| Maximum number of inference units per endpoint | 10 | 
| Maximum throughput per inference unit \(characters\) | 100/second | 
| Maximum throughput per inference unit \(documents\) | 2/second | 
| Maximum number of documents per synchronous request | 1 | 