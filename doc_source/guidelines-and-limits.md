# Guidelines and Limits<a name="guidelines-and-limits"></a>

Keep in mind the following information when using Amazon Comprehend\.

## Supported Regions<a name="limits-regions"></a>

For a list of AWS Regions where Amazon Comprehend is availabe, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html#comprehend_region) in the *Amazon Web Services General Reference*\.

## Throttling<a name="limits-throttling"></a>

For information about throttling for Amazon Comprehend and to request a limit increase, see [ Amazon Comprehend Limits ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend) in the *Amazon Web Services General Reference*\. 

You may be able to avoid throttling by using the batch operations instead of the single transaction operations\. For more information, see [Batch Operations](#limits-batch)\.

## Overall Limits<a name="limits-all"></a>

All operations except topic modeling operations have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Document size \(UTF\-8 characters\) | 5,000 bytes | 

## Batch Operations<a name="limits-batch"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md), [BatchDetectEntities](API_BatchDetectEntities.md), [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md), and [BatchDetectSentiment](API_BatchDetectSentiment.md) operations have the following limits:


| Description | Limit | 
| --- | --- | 
| Documents per request | 25 | 

If you plan to send more than 20 requests per second, you should consider using the batch operations\. Batch operations enable you to send more documents in each request, but have a lower throttling limit\. For more information about throttling limits see [ Amazon Comprehend Limits ](https://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html#limits_amazon_comprehend) in the *Amazon Web Services General Reference*\. For more information about using the batch APIs, see [Batch Processing Documents](how-batch.md)\.

## Language Detection<a name="limits-language-detection"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) and [DetectDominantLanguage](API_DetectDominantLanguage.md) operations have the following limitations:

+ They don't support phonetic language detection\. For example, they will not detect "arigato" as Japanese nor "nihao" as Chinese\.

+ They may have trouble distinguishing close language pairs, such as Indonesian and Malay; or Bosnian, Croation, and Serbian\.

+ For best results the input text should be at least 20 characters long\.

## Topic Modeling<a name="limits-topic-modeling"></a>

Topic detection jobs created with the [StartTopicsDetectionJob](API_StartTopicsDetectionJob.md) operation have the following limits:


| Description | Limit | 
| --- | --- | 
| Character encoding | UTF\-8 | 
| Maximum number of topics to return | 100 | 
| Total size of all files in request | 1 Gb | 
| Maximum file size for one file | 2 Mb | 
| Maximum number of files, one document per file | 50,000 | 
| Maximum number of lines, one document per line | 1,000,000 | 

For best results, you should include at least 1,000 input documents\.