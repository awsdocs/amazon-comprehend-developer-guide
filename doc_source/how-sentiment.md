# Determine Sentiment<a name="how-sentiment"></a>

Use Amazon Comprehend to determine the sentiment of a document\. For example, you can use sentiment analysis to determine the sentiments of comments on a blog posting to determine if your readers liked the post\.

You can determine sentiment for documents in any of the primary languages supported by Amazon Comprehend\. All documents in one job must be in the same language\.

Sentiment determination returns the following values:
+ **Positive** – The text expresses an overall positive sentiment\.
+ **Negative** – The text expresses an overall negative sentiment\.
+ **Mixed** – The text expresses both positive and negative sentiments\.
+ **Neutral** – The text does not express either positive or negative sentiments\.

You can use any of the following API operations to detect the sentiment of a document or a set of documents\.
+ [DetectSentiment](API_DetectSentiment.md)
+ [BatchDetectSentiment](API_BatchDetectSentiment.md)
+ [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md)

The operations return the most likely sentiment for the text as well as the scores for each of the sentiments\. The score represents the likelihood that the sentiment was correctly detected\. For example, in the example below it is 95 percent likely that the text has a `Positive` sentiment\. There is a less than 1 percent likelihood that the text has a `Negative` sentiment\. You can use the `SentimentScore` to determine if the accuracy of the detection meets the needs of your application\.

The `DetectSentiment` operation returns an object that contains the detected sentiment and a [SentimentScore](API_SentimentScore.md) object\. The `BatchDetectSentiment` operation returns a list of sentiments and `SentimentScore` objects, one for each document in the batch\. The `StartSentimentDetectionJob` operation starts an asynchronous job that produces a file containing a list of sentiments and `SentimentScore` objects, one for each document in the job\.

The following example is the response from the `DetectSentiment` operation\.

```
{
"SentimentScore": {
        "Mixed": 0.030585512690246105,
        "Positive": 0.94992071056365967,
        "Neutral": 0.0141543131828308,
        "Negative": 0.00893945890665054
    },
    "Sentiment": "POSITIVE",
    "LanguageCode": "en"
}
```