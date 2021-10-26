# Asynchronous Batch Processing<a name="how-async"></a>

To analyze large documents and large collections of documents, use one of the Amazon Comprehend asynchronous operations\. There is an asynchronous version of each of the Amazon Comprehend operations and an additional set of operations for topic modeling\. 

To analyze a collection of documents, you typically perform the following steps:

1. Store the documents in an Amazon S3 bucket\.

1. Start one or more jobs to analyze the documents\.

1. Monitor the progress of an analysis job\.

1. Retrieve the results of the analysis from an S3 bucket when the job is complete\.

The following sections describe using the Amazon Comprehend API to run asynchronous operations\.

## Prerequisites<a name="detect-topics-role-auth"></a>

Documents must be in UTF\-8\-formatted text files\. You can submit your documents in two formats\. The format you use depends on the type of documents you want to analyze, as described in the following table\.


| Description | Format | 
| --- | --- | 
| Each file contains one input document\. This is best for collections of large documents\. | One document per file | 
|  The input is one or more files\. Each line in a file is considered a document\. This is best for short documents, such as social media postings\. Each line must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. You can't use the UTF\-8 line separator \(u\+2028\) to end a line\.  | One document per line | 

When you start an analysis job, you specify the S3 location for your input data\. The URI must be in the same AWS Region as the API endpoint that you are calling\. The URI can point to a single file or it can be the prefix for a collection of data files\. For more information, see the [InputDataConfig](API_InputDataConfig.md) data type\.

You must grant Amazon Comprehend access to the Amazon S3 bucket that contains your document collection and output files\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Starting an Analysis Job<a name="how-start-job"></a>

To submit an analysis job, use either the Amazon Comprehend console or the appropriate `Start*` operation:
+ [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md)—Start a job to detect the dominant language in each document in the collection\. For more information about the dominant language in a document, see [Detect the Dominant Language](how-languages.md)\.
+ [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md)—Start a job to detect entities in each document in the collection\. For more information about entities, see [Detect Entities](how-entities.md)\.
+ [StartKeyPhrasesDetectionJob](API_StartKeyPhrasesDetectionJob.md)—Start a job to detect key phrases in each document in the collection\. For more information about key phrases, see [Detect Key Phrases](how-key-phrases.md)\.
+ [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md)—Start a job to detect the emotional sentiment in each document in the collection\. For more information about sentiments, see [Determine Sentiment](how-sentiment.md)\.
+ [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md)—Start a job to detect the topics in a document collection\. For more information about topic modeling, see [Topic Modeling](topic-modeling.md)\.

## Monitoring Analysis Jobs<a name="how-monitor-progress"></a>

The `Start*` operation returns an ID that you can use to monitor the job's progress\. 

To monitor progress using the API, you use one of two operations, depending on whether you want to monitor the progress of an individual job or multiple jobs\. 

To monitor the progress of an individual analysis job, use the `Describe*` operations\. You provide the job ID returned by the `Start*` operation\. The response from the `Describe*` operation contains the `JobStatus` field with the job's status\.

To monitor the progress of multiple analysis jobs, use the `List*` operations\. `List*` operations return a list of jobs that you submitted to Amazon Comprehend\. The response includes a `JobStatus` field for each job that tells you the status of the job\.

If the status field is set to `COMPLETED` or `FAILED`, job processing has completed\.

To get the status of individual jobs, use the `Describe*` operation for the analysis that you are performing\.
+ [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md)
+ [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md)
+ [DescribeKeyPhrasesDetectionJob](API_DescribeKeyPhrasesDetectionJob.md)
+ [DescribeSentimentDetectionJob](API_DescribeSentimentDetectionJob.md)
+ [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md)

To get the status of a multiple jobs, use the `List*` operation for the analysis that you are performing\.
+ [ListDominantLanguageDetectionJobs](API_ListDominantLanguageDetectionJobs.md)
+ [ListEntitiesDetectionJobs](API_ListEntitiesDetectionJobs.md)
+ [ListKeyPhrasesDetectionJobs](API_ListKeyPhrasesDetectionJobs.md)
+ [ListSentimentDetectionJobs](API_ListSentimentDetectionJobs.md)
+ [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md)

To restrict the results to jobs that match certain criteria, use the `List*` operations' `Filter` parameter\. You can filter on the job name, the job status, and the date and time that the job was submitted\. For more information, see the `Filter` parameter for each of the `List*` operations in the [Actions](API_Operations.md) reference\.

## Getting Analysis Results<a name="how-get-results"></a>

After an analysis job has finished, use a `Describe*` operation to get the location of the results\. If the job status is `COMPLETED`, the response includes an `OutputDataConfig` field that contains a field with the Amazon S3 location of the output file\. The file, `output.tar.gz`, is a compressed archive that contains the results of the analysis\.

If the status of a job is `FAILED`, the response contains a `Message` field that describes the reason that the analysis job didn't complete successfully\.

To get the status of individual jobs, use the appropriate `Describe*` operation:
+ [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md)
+ [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md)
+ [DescribeKeyPhrasesDetectionJob](API_DescribeKeyPhrasesDetectionJob.md)
+ [DescribeSentimentDetectionJob](API_DescribeSentimentDetectionJob.md)
+ [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md)

The results are returned in a single file, with one JSON structure for each document\. Each response file also includes error messages for any job with the status field set to `FAILED`\.

Each of the following sections shows examples of output for the two input formats\.

### Getting Dominant Language Detection Results<a name="async-dominant-language"></a>

The following is an example of an output file from an analysis that detected the dominant language\. The format of the input is one document per line\. For more information, see the [DetectDominantLanguage](API_DetectDominantLanguage.md) operation\.

```
{"File": "0_doc", "Languages": [{"LanguageCode": "en", "Score": 0.9514502286911011}, {"LanguageCode": "de", "Score": 0.02374090999364853}, {"LanguageCode": "nl", "Score": 0.003208699868991971}, "Line": 0}
{"File": "1_doc", "Languages": [{"LanguageCode": "en", "Score": 0.9822712540626526}, {"LanguageCode": "de", "Score": 0.002621392020955682}, {"LanguageCode": "es", "Score": 0.002386554144322872}], "Line": 1}
```

The following is an example of output from an analysis where the format of the input is one document per file:

```
{"File": "small_doc", "Languages": [{"LanguageCode": "en", "Score": 0.9728053212165833}, {"LanguageCode": "de", "Score": 0.007670710328966379}, {"LanguageCode": "es", "Score": 0.0028472368139773607}]}
{"File": "huge_doc", "Languages": [{"LanguageCode": "en", "Score": 0.984955906867981}, {"LanguageCode": "de", "Score": 0.0026436643674969673}, {"LanguageCode": "fr", "Score": 0.0014206881169229746}]}
```

### Getting Entity Detection Results<a name="async-entities"></a>

The following is an example of an output file from an analysis that detected entities in documents\. The format of the input is one document per line\. For more information, see the [DetectEntities](API_DetectEntities.md) operation\. The output contains two error messages, one for a document that is too long and one for a document that isn't in UTF\-8 format\.

```
{"File": "50_docs", "Line": 0, "Entities": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.9763959646224976, "Text": "Cluj-NapocaCluj-Napoca", "Type": "LOCATION"}"]}
{"File": "50_docs", "Line": 1, "Entities": [{"BeginOffset": 11, "EndOffset": 15, "Score": 0.9615424871444702, "Text": "Maat", "Type": "PERSON"}}]}
{"File": "50_docs", "Line": 2, "ErrorCode": "DOCUMENT_SIZE_EXCEEDED", "ErrorMessage": "Document size exceeds maximum size limit 102400 bytes."}
{"File": "50_docs", "Line": 3, "ErrorCode": "UNSUPPORTED_ENCODING", "ErrorMessage": "Document is not in UTF-8 format and all subsequent lines are ignored."}
```

The following is an example of output from an analysis where the format of the input is one document per file\. The output contains two error messages, one for a document that is too long and one for a document that isn't in UTF\-8 format\. 

```
{"File": "non_utf8.txt", "ErrorCode": "UNSUPPORTED_ENCODING", "ErrorMessage": "Document is not in UTF-8 format and all subsequent line are ignored."}
{"File": "small_doc", "Entities": [{"BeginOffset": 0, "EndOffset": 4, "Score": 0.645766019821167, "Text": "Maat", "Type": "PERSON"}]}
{"File": "huge_doc", "ErrorCode": "DOCUMENT_SIZE_EXCEEDED", "ErrorMessage": "Document size exceeds size limit 102400 bytes."}
```

### Getting Key Phrase Detection Results<a name="async-key-phrases"></a>

The following is an example of an output file from an analysis that detected key phrases in a document\. The format of the input is one document per line\. For more information, see the [DetectKeyPhrases](API_DetectKeyPhrases.md) operation\.

```
{"File": "50_docs", "KeyPhrases": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.8948641419410706, "Text": "Cluj-NapocaCluj-Napoca"}, {"BeginOffset": 45, "EndOffset": 49, "Score": 0.9989854693412781, "Text": "Cluj"}], "Line": 0}            
```

The following is an example of the output from an analysis where the format of the input is one document per file\.

```
{"File": "1_doc", "KeyPhrases": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.8948641419410706, "Text": "Cluj-NapocaCluj-Napoca"}, {"BeginOffset": 45, "EndOffset": 49, "Score": 0.9989854693412781, "Text": "Cluj"}]}            
```

### Getting Sentiment Detection Results<a name="async-sentiment"></a>

The following is an example of an output file from an analysis that detected the sentiment expressed in a document\. It includes an error message because one document is too long\. The format of the input is one document per line\. For more information, see the [DetectSentiment](API_DetectSentiment.md) operation\.

```
{"File": "50_docs", "Line": 0, "Sentiment": "NEUTRAL", "SentimentScore": {"Mixed": 0.002734508365392685, "Negative": 0.008935936726629734, "Neutral": 0.9841893315315247, "Positive": 0.004140198230743408}}
{"File": "50_docs", "Line": 1, "ErrorCode": "DOCUMENT_SIZE_EXCEEDED", "ErrorMessage": "Document size is exceeded maximum size limit 5120 bytes."}
{"File": "50_docs", "Line": 2, "Sentiment": "NEUTRAL", "SentimentScore": {"Mixed": 0.0023119584657251835, "Negative": 0.0029857370536774397, "Neutral": 0.9866572022438049, "Positive": 0.008045154623687267}}
```

The following is an example of the output from an analysis where the format of the input is one document per file\.

```
{"File": "small_doc", "Sentiment": "NEUTRAL", "SentimentScore": {"Mixed": 0.0023450672160834074, "Negative": 0.0009663937962614, "Neutral": 0.9795311689376831, "Positive": 0.017157377675175667}}
{"File": "huge_doc", "ErrorCode": "DOCUMENT_SIZE_EXCEEDED", "ErrorMessage": "Document size is exceeds the limit of 5120 bytes."}
```

### Getting Topic Modeling Results<a name="async-topic-modeling"></a>

Topic modeling analysis returns two files in the `output.tar.gz` file\. For more information, see [Topic Modeling](topic-modeling.md)\.