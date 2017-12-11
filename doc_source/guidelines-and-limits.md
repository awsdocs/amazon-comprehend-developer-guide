# Guidelines and Limits<a name="guidelines-and-limits"></a>

## Guidelines<a name="guidelines"></a>

Amazon Comprehend is available in the following regions:


****  
[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/comprehend/latest/dg/guidelines-and-limits.html)

## Limits<a name="limits"></a>

Amazon Comprehend has the following limits:

+ Documents submitted for topic detection using the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation must be UTF\-8 encoded text files\.

+ The maximum document size is 5,000 bytes of UTF\-8 encoded characters\.

+ The maximum number of documents for the [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [BatchDetectEntities](API_BatchDetectEntities.md), [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md), and [BatchDetectSentiment](API_BatchDetectSentiment.md) operations is 25 documents per request\.

+ The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) and [DetectDominantLanguage](API_DetectDominantLanguage.md) operations have the following limitations:

  + They don't support phonetic language detection\. For example, they will not detect "arigato" as Japanese, nor "nihao" as Chinese\.

  + They may have trouble distinguishing close language pairs, such as Indonesian and Malay; or Bosnian, Croatian, and Serbian\.

  + For best results, the input text should be at least 20 characters long\.

+ Topic detection jobs created with the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation have the following limits:

  + For best results, you should include at least 1,000 input documents\.

  + The maximum number of topics to return can't exceed 100\.

  + The total size of all files in the request can't exceed 1 Gb\.

  + The total size of a single file in the request can't exceed 2 Mb\.

  + When you are using one document per file, you can send a maximum of 50,000 files\.

  + When you are using one document per line, you can send a maximum of 1,000,000 lines\.

  To request a service limit increase, see [https://aws\.amazon\.com/support\.](https://aws.amazon.com/support)\.