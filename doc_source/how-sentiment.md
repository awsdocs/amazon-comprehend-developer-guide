# Detecting Sentiments<a name="how-sentiment"></a>

Use Amazon Comprehend to determine the sentiment of a document\. You can determine if the sentiment is positive, negative, neutral, or mixed\. For example, you can use sentiment analysis to determine the sentiments of comments on a blog posting to determine if your readers liked the post\.

The [DetectSentiment](API_DetectSentiment.md) and [BatchDetectSentiment](API_BatchDetectSentiment.md) operations return the most likely sentiment for the text as well as the scores for each of the sentiments\. The score represents the likelihood that the sentiment was correctly detected\. For example, in the first example below it is 95 percent likely that the text has a `Positive` sentiment\. There is a less than 1 percent likelihood that the text has a `Negative` sentiment\. You can use the `SentimentScore` to determine if the accuracy of the detection meets the needs of your application\.

The following examples show the input text and output from the `DetectSentiment` operation\. The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Positive sentiment:

```
aws comprehend detect-sentiment \
    --endpoint-url endpoint \
    --region region \
    --language-code "en" \
    --text "I feel great this morning."
{
    "SentimentScore": {
        "Mixed": 0.008924853056669235,
        "Positive": 0.9584325551986694,
        "Neutral": 0.026196759194135666,
        "Negative": 0.006445900071412325
    },
    "Sentiment": "POSITIVE",
}
```

Negative sentiment:

```
aws comprehend detect-sentiment \
    --endpoint-url endpoint \
    --region region \
    --language-code "en" \
    --text "This view is horrible."
{
    "SentimentScore": {
        "Mixed": 0.024891886860132217,
        "Positive": 0.050186172127723694,
        "Neutral": 0.1579618602991104,
        "Negative": 0.7669601440429688
    },
    "Sentiment": "NEGATIVE",
}
```

Neutral sentiment:

```
aws comprehend detect-sentiment \
    --endpoint-url endpoint \
    --region region \
    --language-code "en" \
    --text "Childhood is the time to play"
{
    "SentimentScore": {
        "Mixed": 0.020051531493663788,
        "Positive": 0.35540205240249634,
        "Neutral": 0.4203023612499237,
        "Negative": 0.20424406230449677
    },
    "Sentiment": "NEUTRAL",
}
```

Mixed sentiment:

```
aws comprehend detect-sentiment \
    --endpoint-url endpoint \
    --region region \
    --language-code "en" \
    --text "I love Seattle but the winter is too cold for me."
{
    "SentimentScore": {
        "Mixed": 0.5408428907394409,
        "Positive": 0.25948983430862427,
        "Neutral": 0.06789177656173706,
        "Negative": 0.13177546858787537
    },
    "Sentiment": "MIXED",
}
```