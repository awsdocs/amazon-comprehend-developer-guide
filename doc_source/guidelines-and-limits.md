# Guidelines and quotas<a name="guidelines-and-limits"></a>

Unless otherwise specified, the Amazon Comprehend quotas are per region\. You can request an increase to adjustable quotas if needed for your applications\. For information about service quotas and to request a quota increase, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 

**Topics**
+ [Supported Regions](#limits-regions)
+ [Quotas for built\-in models](#limits-builtin-models)
+ [Quotas for custom models](#limits-custom)
+ [Quotas for flywheels](#limits-flywheels)

## Supported Regions<a name="limits-regions"></a>

For a list of AWS Regions where Amazon Comprehend is available, see [ Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend_region) in the *Amazon Web Services General Reference*\.

## Quotas for built\-in models<a name="limits-builtin-models"></a>

Amazon Comprehend provides built\-in models for you to analyze UTF\-8 text documents\. Amazon Comprehend provides synchronous and asynchronous operations that use the built\-in models\.

**Topics**
+ [Real\-time \(synchronous\) analysis](#limits-sync)
+ [Asynchronous analysis](#limits-asynch)

### Real\-time \(synchronous\) analysis<a name="limits-sync"></a>

This section describes quotas related to real\-time analysis using the built\-in models\.

**Topics**
+ [Single document operations](#limits-single)
+ [Multiple document operations](#limits-batch)
+ [Quotas for real\-time \(synchronous\) requests](#limits-throttling)

#### Single document operations<a name="limits-single"></a>

The Amazon Comprehend API provides operations that take a single document as input\. The following quotas apply to these operations\.

##### General quotas for single document operations<a name="limits-sync-general"></a>

The following quotas apply to real\-time analysis for detecting entities, key\-phrases, or dominant language\. For entity detection, these quotas apply to detection with the built\-in models\. For custom entity detection, see the quotas in [Custom entity recognition ](#limits-custom-entity-recognition)\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum document size | 100 KB | 

##### Operation\-specific quotas for single document operations<a name="limits-sync-specific"></a>

The following quotas apply to real\-time analysis for detecting sentiment, targeted sentiment, and syntax\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum document size  | 5 KB | 

#### Multiple document operations<a name="limits-batch"></a>

The Amazon Comprehend API provides batch operations that process multiple documents with a single API request\. The following quotas apply to the batch operations\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum document size | 5 KB | 
| Maximum documents per request | 25 | 

For more information about using the batch document operations, see [Multiple document synchronous processing](concepts-processing-modes.md#how-batch)\.

#### Quotas for real\-time \(synchronous\) requests<a name="limits-throttling"></a>

Amazon Comprehend applies dynamic throttling to synchronous requests\. If system processing bandwidth is available, Amazon Comprehend may process a higher number of your requests than the stated default quota\. Don't rely on the service quotas to control your application's usage of the synchronous API operations\. To control usage, we recommend that you turn on billing alerts or implement rate\-limiting in your application\. 

### Asynchronous analysis<a name="limits-asynch"></a>

This section describes quotas related to asynchronous analysis using the built\-in models\.

**Topics**
+ [General quotas for asynchronous operations](#limits-async-general)
+ [Operation\-specific quotas for asynchronous jobs](#limits-async-specific)
+ [Quotas for asynchronous requests](#limits-async-throttling)

#### General quotas for asynchronous operations<a name="limits-async-general"></a>

You can run asynchronous analysis jobs using the console or any of the API `Start*` operations\. For information about when to use asynchronous operations, see [Asynchronous batch processing](concepts-processing-modes.md#how-async)\. The following quotas apply to most of the API `Start*` operations for built\-in models\. For the exceptions, see [Operation\-specific quotas for asynchronous jobs](#limits-async-specific)\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum size of each document in jobs that detect entities, key phrases, PII, and languages | 1 MB | 
| Maximum total size of all files in a request | 5 GB | 
| Minimum total size of all files in a request | 500 bytes | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum total number of lines, one document per line | 1,000,000 | 

#### Operation\-specific quotas for asynchronous jobs<a name="limits-async-specific"></a>

This section describes quotas for specific asynchronous operations\. If a quota isn't specified in the tables below, the general quota value applies\. 

**Topics**
+ [Sentiment](#limits--sentiment)
+ [Targeted sentiment](#limits-targeted-sentiment)
+ [Events](#limits-events)
+ [Topic modeling](#limits-topic-modeling)

##### Sentiment<a name="limits--sentiment"></a>

Asynchronous sentiment jobs, which you create with the [StartSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartSentimentDetectionJob.html) operation, have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum size of each input document | 5 KB | 

##### Targeted sentiment<a name="limits-targeted-sentiment"></a>

Asynchronous targeted sentiment jobs, which you create with the [StartTargetedSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartTargetedSentimentDetectionJob.html) operation, have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Supported document formats | UTF\-8 | 
| Maximum size of each document in a job | 10 KB | 
| Maximum size of all documents in a job | 300 MB | 
| Maximum number of files, one document per file | 30,000 | 
| Maximum total number of lines, one document per line \(for all files in a request\) | 30,000 | 

##### Events<a name="limits-events"></a>

Asynchronous events detection jobs, which you create with the [StartEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEventsDetectionJob.html) operation, have the following quotas\.


| Description | Quotas | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Total size of all files in a job | 50 MB | 
| Maximum size of each document in a job | 10 KB | 
| Maximum number of files, one document per file | 5,000 | 
| Maximum total number of lines, one document per line \(for all files in request\) | 5,000 | 

##### Topic modeling<a name="limits-topic-modeling"></a>

Asynchronous topic modeling jobs, which you create with the [StartTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartTopicsDetectionJob.html) operation, have the following quotas\.


| Description | Quota/Guideline | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of topics to return | 100 | 
| Maximum file size for one file, one document per file | 100 MB | 

For more information, see [Topic modeling](topic-modeling.md)

#### Quotas for asynchronous requests<a name="limits-async-throttling"></a>

Each Amazon Comprehend API operation supports a default maximum number of requests per second \(per region, per account\) for asynchronous operations\. For information about these quotas, see [ Amazon Comprehend endpoints and quotas ](https://docs.aws.amazon.com/general/latest/gr/comprehend.html) in the *Amazon Web Services General Reference*\.

You create new analysis jobs using the Amazon Comprehend console or API\. Each account can have up to 10 concurrent active jobs of a given job type\. 

## Quotas for custom models<a name="limits-custom"></a>

You can use Amazon Comprehend to build your own custom models for custom classification and custom entity recognition\. This section provides the guidelines and quotas related to training and using custom models\. For more information about custom models, see [Amazon Comprehend Custom](concepts-custom.md)\.

**Topics**
+ [General quotas](#limits-custom-general)
+ [Quotas for endpoints](#limits-custom-endpoints)
+ [Document classification](#limits-document-classification)
+ [Custom entity recognition](#limits-custom-entity-recognition)

### General quotas<a name="limits-custom-general"></a>

Amazon Comprehend sets general size quotas for each type of input document that you can analyze with custom models\. For real\-time analysis quotas, see [Maximum document sizes for real\-time analysis](idp-inputs-sync.md#idp-inputs-sync-sizes)\. For asynchronous analysis quotas, see [Inputs for asynchronous custom analysis](idp-inputs-async.md)\.

### Quotas for endpoints<a name="limits-custom-endpoints"></a>

You create an endpoint to run real\-time analysis with a custom model\. For information about endpoints, see [Managing Amazon Comprehend endpoints](manage-endpoints.md)\.

The following quotas apply to the endpoints\. For information about how to request a quota increase, see [AWS Service Quotas](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html)\. 


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of active endpoints per Region for each account | 10 | 
| Maximum number of inference units per Region for each account | 100 | 
| Maximum number of inference units per endpoint | 10 | 
| Maximum throughput per inference unit \(characters\) | 100/second | 
| Maximum throughput per inference unit \(documents\) | 2/second | 

### Document classification<a name="limits-document-classification"></a>

This section describes the guidelines and quotas for the following document classification operations:
+ Classifier training jobs that you start with the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) operation\.
+ Asynchronous document classification jobs that you start with the [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html) operation\.
+ Synchronous document classification requests that use the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) operation\.

#### Classification for plain text documents<a name="limits-class-plaintext"></a>

Amazon Comprehend provides async and sync operations to classify plain text documents\.

##### Training<a name="limits-class-p-training"></a>

The following table describes quotas related to training a custom classifier with plain text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum length of class name | 5,000 characters | 
| Maximum number of classes \(multi\-class mode\) | 1,000 | 
| Maximum number of classes \(multi\-label mode\) | 100 | 
| Minimum number of training documents per class \(multi\-class mode\) | 50 | 
| Minimum number of training documents per class \(multi\-label mode\) | 10 | 
| Minimum number of training documents \(multi\-label mode\) | 50 | 
| Total size of all files in training job | 5 GB | 
| Maximum number of augmented manifest files for training a custom classifier | 5 | 
| Maximum number of attribute names for each augmented manifest file | 5 | 
| Maximum length of attribute name | 63 characters | 

##### Real\-time \(synchronous\) analysis<a name="limits-class-p-sync"></a>

The following table describes quotas related to real\-time classification of plain text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of documents per synchronous request | 1 | 
| Maximum text document size \(UTF\-8 encoded\) | 10 KB | 

##### Asynchronous analysis<a name="limits-class-p-async"></a>

The following table describes quotas related to asynchronous classification of plain text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Total size of all files in asynchronous job | 5 GB | 
| Maximum file size for one file, one document per file | 10 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum total number of lines, one document per line \(for all files in request\) | 1,000,000 | 

#### Classification for semi\-structured documents<a name="limits-class-structured"></a>

This section describes the guidelines and quotas for document classification of semi\-structured documents\. To classify semi\-structured documents, use a custom model that you trained with plain text documents\.

##### Real\-time \(synchronous\) analysis<a name="limits-class-s-sync"></a>

This section describes quotas related to real\-time classification of semi\-structured documents\.

The following table shows the maximum file sizes for input documents\. For all input document types, the input file maximum is one page, with no more than 10,000 characters\.


| File type | Maximum size \(API\) | Maximum size \(console\) | 
| --- | --- | --- | 
| UTF\-8 text documents | 10 KB | 10 KB | 
| PDF documents | 10 MB | 5 MB | 
| Word documents | 10 MB | 5 MB | 
| Image files | 10 MB | 5 MB | 
| Textract output files | 1 MB | n/a | 

##### Asynchronous analysis<a name="limits-class-s-async"></a>

The following table describes quotas related to asynchronous classification of semi\-structured documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(PDF\) | 1 byte–50 MB | 
| Document size \(Docx\) | 1 byte–5 MB | 
| Image size \(JPG or PNG\) | 1 byte–10 MB | 
| Image size \(TIFF\) | 1 byte–10 MB\. Maximum one page\. | 
| Maximum number of files | 500 | 
| Maximum number of pages for a PDF or Docx file | 100 | 
| Document corpus size after text extraction \(plaintext, all files combined\) | 1 byte–5 GB | 

### Custom entity recognition<a name="limits-custom-entity-recognition"></a>

This section describes the guidelines and quotas for the following operations for custom entity recognition:
+ Entity recognizer training jobs started with the [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEntityRecognizer.html) operation\.
+ Asynchronous entity recognition jobs started with the [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEntitiesDetectionJob.html) operation\.
+ Synchronous entity recognition requests using the [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) operation\.

#### Custom entity recognition for plain text documents<a name="limits-cer-plaintext"></a>

Amazon Comprehend provides async and sync operations to analyze plain text documents with a custom entity recognizer\. 

##### Training<a name="limits-cer-p-training"></a>

This section describes quotas related to training a custom entity recognizer to analyze plain text documents\. To train the model, you can provide an entity list or a set of annotated text documents\.

The following table describes quotas related to training the model with an entity list\.


| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model | 1–25 | 
| Document size \(UTF\-8\) | 1–5,000 byte | 
| Number of items in entity list | 1–1 million | 
| Length of individual entry \(post\-strip\) in entry list | 1–5,000 | 
| Entity list corpus size \(all docs in plaintext combined\) | 5 KB –200 MB | 

The following table describes quotas related to training the model with annotated text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1–25 | 
| Document size \(UTF\-8\) | 1–5,000 byte | 
| Number of documents \(see [Plain\-text annotations](cer-annotation.md#prep-training-data-ann)\) | 3–200,000 | 
| Document corpus size \(all docs in plaintext combined\) | 5 KB \- 200 MB | 
| Minimum number of annotations per entity | 25 | 

##### Real\-time \(synchronous\) analysis<a name="limits-cer-p-sync"></a>

The following table describes quotas related to real\-time analysis of plain text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of documents per synchronous request | 1 | 
| Maximum text document size \(UTF\-8 encoded\) | 5 KB | 

##### Asynchronous analysis<a name="limits-cer-p-async"></a>

The following table describes quotas related to asynchronous entity recognition of plain text documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(UTF\-8\) | 1 byte–1 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum total number of lines, one document per line \(for all files in request\) | 1,000,000 | 
| Document corpus size \(all docs in plaintext combined\) | 1 byte–5 GB | 

#### Custom entity recognition for semi\-structured documents<a name="limits-cer-structured"></a>

Amazon Comprehend provides async and sync operations to analyze semi\-structured documents with a custom entity recognizer\. You need to train the model using annotated PDF documents\.

##### Training<a name="limits-cer-s-training"></a>

The following table describes quotas related to training a custom entity recognizer \(CreateEntityRecognizer\) to analyze semi\-structured documents\.


| Description | Quota/Guideline | 
| --- | --- | 
| Number of entities per model/custom entity recognizer | 1–25 | 
| Maximum annotation file size \(UTF\-8 JSON\) | 5 MB | 
| Number of documents | 250–10,000 | 
| Document corpus size \(all docs in plaintext combined\) | 5 KB–1 GB | 
| Minimum number of annotations per entity | 100 | 
| Maximum number of augmented manifest files for training a custom entity recognizer | 5 | 
| Maximum number of attribute names for each augmented manifest file | 5 | 
| Maximum length of attribute name | 63 characters | 

##### Real\-time \(synchronous\) analysis<a name="limits-cer-s-sync"></a>

This section describes quotas related to real\-time analysis of semi\-structured documents\. 

The following table shows the maximum file sizes for input documents\. For all input document types, the input file maximum is one page, with no more than 10,000 characters\.


| File type | Maximum size \(API\) | Maximum size \(console\) | 
| --- | --- | --- | 
| UTF\-8 text documents | 10 KB | 10 KB | 
| PDF documents | 10 MB | 5 MB | 
| Word documents | 10 MB | 5 MB | 
| Image files | 10 MB | 5 MB | 
| Textract output files | 1 MB | n/a | 

##### Asynchronous analysis<a name="limits-cer-s-async"></a>

This section describes quotas for asynchronous analysis of semi\-structured documents\. 


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

## Quotas for flywheels<a name="limits-flywheels"></a>

Use flywheels to manage training and tracking of custom model versions for custom classification and custom entity recognition\. For more information about Flywheels, see [Flywheels](flywheels.md)\.

### General quotas for flywheels<a name="limits-flywheels-general"></a>

The follow quotas apply to flywheels and flywheel iterations\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum number of flywheels | 50  | 
| Maximum number of flywheels in CREATING state | 10 | 
| Maximum number of training datasets per flywheel | 50 | 
| Maximum number of test datasets per flywheel | 10 | 
| Maximum number of datasets with INGESTING status | 10 | 
| Maximum number of in\-progress flywheel iterations per account | 10 | 

### Dataset quotas for custom classification models<a name="limits-flywheels-class"></a>

When you ingest a dataset for a flywheel associated with a custom classification model, the following quotas apply\.


| Description | Quota/Guideline | 
| --- | --- | 
| Minimum number of training documents per class \(multi\-label mode\) | 50 | 
| Maximum number of training documents | 1,000,000 | 
| Minimum dataset size | 500 bytes | 
| Maximum dataset size | 5 GB | 
| Maximum file size for one file, one document per file | 10 MB | 

### Dataset quotas for custom entity recognition models<a name="limits-flywheels-class"></a>

When you ingest a dataset for a flywheel associated with a custom entity recognition model, the following quotas apply\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum document size | 5 KB | 
| Minimum number of training documents | 3 | 
| Maximum number of training documents | 200,000 | 
| Minimum number of annotations per entity | 25 | 
| Maximum dataset size | 200 MB | 