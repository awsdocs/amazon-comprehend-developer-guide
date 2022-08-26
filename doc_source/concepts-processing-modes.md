# Document processing modes<a name="concepts-processing-modes"></a>

Amazon Comprehend supports three document processing modes\. Your choice of mode depends on the number documents you need to process and how immediately you need to view the results:
+ **Single\-document synchronous** – You call Amazon Comprehend with a single document and receive a synchronous response, delivered to your application \(or the console\) right away\. 
+ **Multi\-document synchronous** – You call the Amazon Comprehend API with a collection of up to 25 documents and receive a synchronous response\.
+ **Asynchronous batch** – For a large collection of documents, put the documents into an Amazon S3 bucket and start an asynchronous job \(using console or API operations\) to analyze the documents\. Amazon Comprehend stores the results of the analysis in the S3 bucket/folder that you specify in the request\.

**Topics**
+ [Single\-document processing](#how-single)
+ [Multiple document synchronous processing](#how-batch)
+ [Asynchronous batch processing](#how-async)

## Single\-document processing<a name="how-single"></a>

Single\-document operations are synchronous operations that return the results of the document analysis directly to your application\. Use single\-document synchronous operations when you are creating an interactive application that works on one document at a time\.

For more information about the synchronous API operations, see [Real\-time analysis using the built\-in models](realtime-console-analysis.md) \(for console\) and [Real\-time analysis using the API](using-api-sync.md)\.

## Multiple document synchronous processing<a name="how-batch"></a>

When you have multiple documents that you want to process, you can use the `Batch*` API operations to send more than one document to Amazon Comprehend at a time\. You can send up to 25 documents in each request\. Amazon Comprehend sends back a list of responses, one for each document in the request\. Requests made with these operations are synchronous\. Your application calls the operation and then waits for the response from the service\. 

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

For more information about the synchronous batch API operations, see [Real\-time batch APIs](using-api-sync.md#get-started-batch)\.

## Asynchronous batch processing<a name="how-async"></a>

To analyze large documents and large collections of documents, use the Amazon Comprehend asynchronous operations\.

To analyze a collection of documents, you typically perform the following steps:

1. Store the documents in an Amazon S3 bucket\.

1. Start one or more analysis jobs to analyze the documents\.

1. Monitor the progress of the analysis jobs\.

1. Retrieve the results of the analysis from an S3 bucket when the job is complete\.

For more information about using the asynchronous API operations, see [Running analysis jobs using the console](analysis-jobs.md) \(console\) and [Async analysis jobs using the API](api-async.md)\.