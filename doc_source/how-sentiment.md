# Determine Sentiment<a name="how-sentiment"></a>

Use Amazon Comprehend to determine the sentiment of a document\. You can determine if the sentiment is positive, negative, neutral, or mixed\. For example, you can use sentiment analysis to determine the sentiments of comments on a blog posting to determine if your readers liked the post\.

Determine sentiment operations can be performed using any of the primary languages supported by Amazon Comprehend\. All documents must be in the same language\.

You can use any of the following operations to detect the sentiment of a document or a set of documents\.
+ [ DetectSentiment ](API_DetectSentiment.md)
+ [ BatchDetectSentiment ](API_BatchDetectSentiment.md)
+ [ StartSentimentDetectionJob ](API_StartSentimentDetectionJob.md)

The operations return the most likely sentiment for the text as well as the scores for each of the sentiments\. The score represents the likelihood that the sentiment was correctly detected\. For example, in the example below it is 95 percent likely that the text has a `Positive` sentiment\. There is a less than 1 percent likelihood that the text has a `Negative` sentiment\. You can use the `SentimentScore` to determine if the accuracy of the detection meets the needs of your application\.

The `DetectSentiment` operation returns an object that contains the detected sentiment and a [ SentimentScore ](API_SentimentScore.md) object\. The `BatchDetectSentiment` operation returns a list of sentiments and `SentimentScore` objects, one for each document in the batch\. The `StartSentimentDetectionJob` operation starts an asynchronous job that produces a file containing a list of sentiments and `SentimentScore` objects, one for each document in the job\.

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