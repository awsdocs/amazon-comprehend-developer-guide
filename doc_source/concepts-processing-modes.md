# Document processing modes<a name="concepts-processing-modes"></a>

When evaluating your documents, you can use one of several methods to process them, depending on the number documents you have and how you want to view the results:
+ **Single\-document synchronous** —You call Amazon Comprehend with a single document and receive a synchronous response, delivered to your application right away\. 
+ **Multi\-document synchronous** —You call Amazon Comprehend with a collection of up to 25 documents and receive a synchronous response\.
+ **Asynchronous batch** —You put a collection of documents into an Amazon S3 bucket and start an asynchronous operation to analyze the documents\. The results of the analysis are returned in an S3 bucket\.

**Topics**
+ [Single\-document processing](#how-single)
+ [Multiple document synchronous processing](#how-batch)
+ [Asynchronous batch processing](#how-async)

## Single\-document processing<a name="how-single"></a>

The single\-document operations are synchronous operations that return the results of analyzing the document directly to your application\. You should use the single\-document operations when you are creating an interactive application that works on one document at a time\.

You can use the following single\-document operations:
+ [DetectDominantLanguage](API_DetectDominantLanguage.md)
+ [DetectEntities](API_DetectEntities.md)
+ [DetectKeyPhrases](API_DetectKeyPhrases.md)
+ [DetectPiiEntities](API_DetectPiiEntities.md)
+ [ContainsPiiEntities](API_ContainsPiiEntities.md)
+ [DetectSentiment](API_DetectSentiment.md)
+ [DetectSyntax](API_DetectSyntax.md)

## Multiple document synchronous processing<a name="how-batch"></a>

When you have multiple documents that you want to process, you can use the `Batch*` operations to send more than one document to Amazon Comprehend at a time\. You can send up to 25 documents in each request\. Amazon Comprehend sends back a list of responses, one for each document in the request\. 

You can use the following operations to process multiple documents in a single request\. Requests made with these operations are synchronous\. Your application calls the operation and then waits for the response from the service\. 
+ [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md)
+ [BatchDetectEntities](API_BatchDetectEntities.md)
+ [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md)
+ [BatchDetectSentiment](API_BatchDetectSentiment.md)
+ [BatchDetectSyntax](API_BatchDetectSyntax.md)

Using the `Batch*` operations is identical to calling the single document APIs for each of the documents in the request\. Using these APIs can result in better performance for your applications\.

The input to each of the APIs is a JSON structure containing the documents to process\. For all operations except `BatchDetectDominantLanguage`, you must set the input language\. You can set only one input language for each request\. For example, the following is the input to the `BatchDetectEntities` operation\. It contains two documents and is in English\.

```
{
   "LanguageCode": "en",
   "TextList": [
      "I have been living in Seattle for almost 4 years",
      "It is raining today in Seattle"
   ]
}
```

The response from a `Batch*` operation contains two lists, the `ResultList` and the `ErrorList`\. The `ResultList` contains one record for each document that was successfully processed\. The result for each document in the request is identical to the result you would get if you ran a single document operation on the document\. The results for each document are assigned an index based on the order of the documents in the input file\. The response from the `BatchDetectEntities` operation is:

```
{
   "ResultList"  : [
      {
         "Index": 0,
         "Entities": [
            {
               "Text": "Seattle", 
               "Score": 0.95, 
               "Type": "LOCATION", 
               "BeginOffset": 22, 
               "EndOffset": 29
            },
            {
               "Text": "almost 4 years", 
               "Score": 0.89, 
               "Type": "QUANTITY", 
               "BeginOffset": 34, 
               "EndOffset": 48
            }
         ]
      },
      {
         "Index": 1,
         "Entities": [
            {
              "Text": "today",
              "Score": 0.87,
              "Type": "DATE",
              "BeginOffset": 14,
              "EndOffset": 19
            },
            {
               "Text": "Seattle",
               "Score": 0.96,
               "Type": "LOCATION",
               "BeginOffset": 23,
               "EndOffset": 30
            }
         ]
      }
   ],
   "ErrorList": []
}
```

When an error occurs in the request the response contains an `ErrorList` that identifies the documents that contained an error\. The document is identified by its index in the input list\. For example, the following input to the `BatchDetectLanguage` operation contains a document that cannot be processed:

```
{
   "TextList": [
     "hello friend", 
     "$$$$$$",
     "hola amigo"
   ]       
}
```

The response from Amazon Comprehend includes an error list that identifies the document that contained an error:

```
{
    "ResultList": [
        {
          "Index": 0,
          "Languages":[
            {
              "LanguageCode":"en",
              "Score": 0.99
            }
          ]
        },
        {
          "Index": 2
          "Languages":[
            {
              "LanguageCode":"es",
              "Score": 0.82
            }
          ]
        }
    ],
    "ErrorList": [
      {
        "Index": 1,
        "ErrorCode": "InternalServerException",
        "ErrorMessage": "Unexpected Server Error. Please try again."
      }
    ]
}
```

## Asynchronous batch processing<a name="how-async"></a>

To analyze large documents and large collections of documents, use one of the Amazon Comprehend asynchronous operations\. There is an asynchronous version of each of the Amazon Comprehend operations and an additional set of operations for topic modeling\. 

To analyze a collection of documents, you typically perform the following steps:

1. Store the documents in an Amazon S3 bucket\.

1. Start one or more jobs to analyze the documents\.

1. Monitor the progress of an analysis job\.

1. Retrieve the results of the analysis from an S3 bucket when the job is complete\.

The following sections describe using the Amazon Comprehend API to run asynchronous operations\.

### Prerequisites<a name="detect-topics-role-auth"></a>

Documents must be in UTF\-8\-formatted text files\. You can submit your documents in two formats\. The format you use depends on the type of documents you want to analyze, as described in the following table\.


| Description | Format | 
| --- | --- | 
| Each file contains one input document\. This is best for collections of large documents\. | One document per file | 
|  The input is one or more files\. Each line in a file is considered a document\. This is best for short documents, such as social media postings\. Each line must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. You can't use the UTF\-8 line separator \(u\+2028\) to end a line\.  | One document per line | 

When you start an analysis job, you specify the S3 location for your input data\. The URI must be in the same AWS Region as the API endpoint that you are calling\. The URI can point to a single file or it can be the prefix for a collection of data files\. For more information, see the [InputDataConfig](API_InputDataConfig.md) data type\.

You must grant Amazon Comprehend access to the Amazon S3 bucket that contains your document collection and output files\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.

### Starting an analysis job<a name="how-start-job"></a>

To submit an analysis job, use either the Amazon Comprehend console or the appropriate `Start*` operation:
+ [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md) — Start a job to detect the dominant language in each document in the collection\. For more information about the dominant language in a document, see [Dominant language](how-languages.md)\.
+ [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) — Start a job to detect entities in each document in the collection\. For more information about entities, see [Entities](how-entities.md)\.
+ [StartEventsDetectionJob](API_StartEventsDetectionJob.md) — Start a job to detect events in each document in the collection\. For more information about entities, see [Events](how-events.md)\.
+ [StartKeyPhrasesDetectionJob](API_StartKeyPhrasesDetectionJob.md) — Start a job to detect key phrases in each document in the collection\. For more information about key phrases, see [Key phrases](how-key-phrases.md)\.
+ [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md) — Start a job to detect personally identifiable information \(PII\) in each document in the collection\. For more information about PII, see [Detecting PII entities](how-key-phrases.md)\.
+ [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md) — Start a job to detect the sentiment in each document in the collection\. For more information about sentiments, see [Sentiment](how-sentiment.md)\.
+ [StartTargetedSentimentDetectionJob](API_StartTargetedSentimentDetectionJob.md) — Start a job to detect the sentiment of specific entities in each document in the collection\. For more information, see [Targeted sentiment](how-targeted-sentiment.md)\.
+ [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) — Start a job to detect the topics in a document collection\. For more information about topic modeling, see [Topic modeling](topic-modeling.md)\.

### Monitoring analysis jobs<a name="how-monitor-progress"></a>

The `Start*` operation returns an ID that you can use to monitor the job's progress\. 

To monitor progress using the API, you use one of two operations, depending on whether you want to monitor the progress of an individual job or multiple jobs\. 

To monitor the progress of an individual analysis job, use the `Describe*` operations\. You provide the job ID returned by the `Start*` operation\. The response from the `Describe*` operation contains the `JobStatus` field with the job's status\.

To monitor the progress of multiple analysis jobs, use the `List*` operations\. `List*` operations return a list of jobs that you submitted to Amazon Comprehend\. The response includes a `JobStatus` field for each job that tells you the status of the job\.

If the status field is set to `COMPLETED` or `FAILED`, job processing has completed\.

To get the status of individual jobs, use the `Describe*` operation for the analysis that you are performing\.
+ [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md)
+ [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md)
+ [DescribeEventsDetectionJob](API_DescribeEventsDetectionJob.md)
+ [DescribeKeyPhrasesDetectionJob](API_DescribeKeyPhrasesDetectionJob.md)
+ [DescribePiiEntitiesDetectionJob](API_DescribePiiEntitiesDetectionJob.md)
+ [DescribeSentimentDetectionJob](API_DescribeSentimentDetectionJob.md)
+ [DescribeTargetedSentimentDetectionJob](API_DescribeTargetedSentimentDetectionJob.md)
+ [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md)

To get the status of a multiple jobs, use the `List*` operation for the analysis that you are performing\.
+ [ListDominantLanguageDetectionJobs](API_ListDominantLanguageDetectionJobs.md)
+ [ListEntitiesDetectionJobs](API_ListEntitiesDetectionJobs.md)
+ [ListEventsDetectionJobs](API_ListEventsDetectionJobs.md)
+ [ListKeyPhrasesDetectionJobs](API_ListKeyPhrasesDetectionJobs.md)
+ [ListPiiEntitiesDetectionJobs](API_ListPiiEntitiesDetectionJobs.md)
+ [ListSentimentDetectionJobs](API_ListSentimentDetectionJobs.md)
+ [ListTargetedSentimentDetectionJobs](API_ListTargetedSentimentDetectionJobs.md)
+ [ListTopicsDetectionJobs](API_ListTopicsDetectionJobs.md)

To restrict the results to jobs that match certain criteria, use the `List*` operations' `Filter` parameter\. You can filter on the job name, the job status, and the date and time that the job was submitted\. For more information, see the `Filter` parameter for each of the `List*` operations in the [Actions](API_Operations.md) reference\.

### Getting analysis results<a name="how-get-results"></a>

After an analysis job has finished, use a `Describe*` operation to get the location of the results\. If the job status is `COMPLETED`, the response includes an `OutputDataConfig` field that contains a field with the Amazon S3 location of the output file\. The file, `output.tar.gz`, is a compressed archive that contains the results of the analysis\.

If the status of a job is `FAILED`, the response contains a `Message` field that describes the reason that the analysis job didn't complete successfully\.

To get the status of individual jobs, use the appropriate `Describe*` operation:
+ [DescribeDominantLanguageDetectionJob](API_DescribeDominantLanguageDetectionJob.md)
+ [DescribeEntitiesDetectionJob](API_DescribeEntitiesDetectionJob.md)
+ [DescribeEventsDetectionJob](API_DescribeEventsDetectionJob.md)
+ [DescribeKeyPhrasesDetectionJob](API_DescribeKeyPhrasesDetectionJob.md)
+ [DescribeSentimentDetectionJob](API_DescribeSentimentDetectionJob.md)
+ [DescribeTargetedSentimentDetectionJob](API_DescribeTargetedSentimentDetectionJob.md)
+ [DescribeTopicsDetectionJob](API_DescribeTopicsDetectionJob.md)

The results are returned in a single file, with one JSON structure for each document\. Each response file also includes error messages for any job with the status field set to `FAILED`\.

Each of the following sections shows examples of output for the two input formats\.

#### Getting dominant language detection results<a name="async-dominant-language"></a>

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

#### Getting entity detection results<a name="async-entities"></a>

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

#### Getting events detection results<a name="async-events"></a>

The following is an example an output file from an analysis job that detected events in documents\. The format of the input is one document per line\. 

```
{"Entities": [{"Mentions": [{"BeginOffset": 12, "EndOffset": 27, "GroupScore": 1.0, "Score": 0.916355, "Text": "over a year ago", "Type": "DATE"}]}, {"Mentions": [{"BeginOffset": 33, "EndOffset": 39, "GroupScore": 1.0, "Score": 0.996603, "Text": "Amazon", "Type": "ORGANIZATION"}]}, {"Mentions": [{"BeginOffset": 66, "EndOffset": 77, "GroupScore": 1.0, "Score": 0.999283, "Text": "Whole Foods", "Type": "ORGANIZATION"}]}], "Events": [{"Arguments": [{"EntityIndex": 2, "Role": "INVESTEE", "Score": 0.999283}, {"EntityIndex": 0, "Role": "DATE", "Score": 0.916355}, {"EntityIndex": 1, "Role": "INVESTOR", "Score": 0.996603}], "Triggers": [{"BeginOffset": 373, "EndOffset": 380, "GroupScore": 0.999984, "Score": 0.999955, "Text": "acquire", "Type": "CORPORATE_ACQUISITION"}], "Type": "CORPORATE_ACQUISITION"}, {"Arguments": [{"EntityIndex": 2, "Role": "PARTICIPANT", "Score": 0.999283}], "Triggers": [{"BeginOffset": 115, "EndOffset": 123, "GroupScore": 1.0, "Score": 0.999967, "Text": "combined", "Type": "CORPORATE_MERGER"}], "Type": "CORPORATE_MERGER"}], "File": "doc.txt", "Line": 0}
```

For more information about events output file structure and supported event types, see [Events](how-events.md)\.

#### Getting key phrase detection results<a name="async-key-phrases"></a>

The following is an example of an output file from an analysis that detected key phrases in a document\. The format of the input is one document per line\. For more information, see the [DetectKeyPhrases](API_DetectKeyPhrases.md) operation\.

```
{"File": "50_docs", "KeyPhrases": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.8948641419410706, "Text": "Cluj-NapocaCluj-Napoca"}, {"BeginOffset": 45, "EndOffset": 49, "Score": 0.9989854693412781, "Text": "Cluj"}], "Line": 0}            
```

The following is an example of the output from an analysis where the format of the input is one document per file\.

```
{"File": "1_doc", "KeyPhrases": [{"BeginOffset": 0, "EndOffset": 22, "Score": 0.8948641419410706, "Text": "Cluj-NapocaCluj-Napoca"}, {"BeginOffset": 45, "EndOffset": 49, "Score": 0.9989854693412781, "Text": "Cluj"}]}            
```

#### Getting personally identifiable information \(PII\) detection results<a name="async-pii"></a>

The following is an example an output file from an analysis job that detected PII entities in documents\. The format of the input is one document per line\. 

```
{"Entities":[{"Type":"NAME","BeginOffset":40,"EndOffset":69,"Score":0.999995},{"Type":"ADDRESS","BeginOffset":247,"EndOffset":253,"Score":0.998828},{"Type":"BANK_ACCOUNT_NUMBER","BeginOffset":406,"EndOffset":411,"Score":0.693283}],"File":"doc.txt","Line":0}
{"Entities":[{"Type":"SSN","BeginOffset":1114,"EndOffset":1124,"Score":0.999999},{"Type":"EMAIL","BeginOffset":3742,"EndOffset":3775,"Score":0.999993},{"Type":"PIN","BeginOffset":4098,"EndOffset":4102,"Score":0.999995}],"File":"doc.txt","Line":1}
```

The following is an example of output from an analysis where the format of the input is one document per file\.

```
{"Entities":[{"Type":"NAME","BeginOffset":40,"EndOffset":69,"Score":0.999995},{"Type":"ADDRESS","BeginOffset":247,"EndOffset":253,"Score":0.998828},{"Type":"BANK_ROUTING","BeginOffset":279,"EndOffset":289,"Score":0.999999}],"File":"doc.txt"}
```

#### Getting sentiment detection results<a name="async-sentiment"></a>

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

#### Getting topic modeling results<a name="async-topic-modeling"></a>

Topic modeling analysis returns two files in the `output.tar.gz` file\. For more information, see [Topic modeling](topic-modeling.md)\.