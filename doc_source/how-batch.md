# Batch Processing Documents<a name="how-batch"></a>

When you have multiple documents that you want to process, you can use batch operations to send more than one document to Amazon Comprehend at a time\. You can send up to 25 documents in each batch\. Amazon Comprehend sends back a list of responses, one for each document in the batch\. 

Using the batch operations is identical to calling the single document APIs for each of the documents in the request\. Calling the batch APIs can result in better performance for your applications\.

The input to the batch APIs is a JSON structure containing the documents to process\. For all operations except `BatchDetectDominantLanguage`, you must set the input language\. You can set only one input language for each batch\. For example, the following is the input to the `BatchDetectEntities` operation\. It contains two documents and is in English\.

```
{
   "LanguageCode": "en",
   "TextList": [
      "I have been living in Seattle for almost 4 years",
      "It is raining today in Seattle"
   ]
}
```

The response from a batch operation contains two lists, the `ResultList` and the `ErrorList`\. The `ResultList` contains one record for each document that was successfully processed\. The result for each document in the batch is identical to the result you would get if you ran a single document operation on the document\. The results for each document are assigned an index based on the order of the documents in the input file\. The response from the `BatchDetectEntities` operation is:

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

When an error occurs in the batch request the response contains an `ErrorList` that identifies the documents that contained an error\. The document is identified by its index in the input list\. For example, the following input to the `BatchDetectLanguage` operation contains a document that cannot be processed:

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