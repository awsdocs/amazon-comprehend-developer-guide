# Detecting Sentiment<a name="get-started-api-sentiment"></a>

To determine the overall emotional tone of text, use the [DetectSentiment](API_DetectSentiment.md) operation\. To detect the sentiment in up to 25 documents in a batch, use the [BatchDetectSentiment](API_BatchDetectSentiment.md) operation\. For more information, see [Using the Batch APIs](get-started-batch.md)\.


+ [Detecting Sentiment Using the AWS Command Line Interface](#get-started-api-sentiment-cli)
+ [Detecting Sentiment Using the AWS SDK for Java](#get-started-api-sentiment-java)
+ [Detecting Sentiment Using the AWS SDK for Python \(Boto\)](#get-started-api-sentiment-python)

## Detecting Sentiment Using the AWS Command Line Interface<a name="get-started-api-sentiment-cli"></a>

The following example demonstrates using the `DetectSentiment` operation with the AWS CLI\. This example specifies the language of the input text\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-sentiment \
    --region region \
    --language-code "en" \
    --text "It is raining today in Seattle."
```

 Amazon Comprehend responds with the following:

```
{
    "SentimentScore": {
        "Mixed": 0.014585512690246105,
        "Positive": 0.31592071056365967,
        "Neutral": 0.5985543131828308,
        "Negative": 0.07093945890665054
    },
    "Sentiment": "NEUTRAL",
    "LanguageCode": "en"
}
```

## Detecting Sentiment Using the AWS SDK for Java<a name="get-started-api-sentiment-java"></a>

The following example Java program detects the sentiment of input text\. You must specify the language of the input text\. 

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectSentimentRequest;
import com.amazonaws.services.comprehend.model.DetectSentimentResult;

public class App 
{
    public static void main( String[] args )
    {

        String text = "It is raining today in Seattle";

        // Create credentials using a provider chain. For more information, see
        // https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
        AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();
 
        AmazonComprehend comprehendClient =
            AmazonComprehendClientBuilder.standard()
                                         .withCredentials(awsCreds)
                                         .withRegion("region")
                                         .build();
                                         
        // Call detectSentiment API
        System.out.println("Calling DetectSentiment");
        DetectSentimentRequest detectSentimentRequest = new DetectSentimentRequest().withText(text)
                                                                                    .withLanguageCode("en");
        DetectSentimentResult detectSentimentResult = comprehendClient.detectSentiment(detectSentimentRequest);
        System.out.println(detectSentimentResult);
        System.out.println("End of DetectSentiment\n");
        System.out.println( "Done" );
    }
}
```

## Detecting Sentiment Using the AWS SDK for Python \(Boto\)<a name="get-started-api-sentiment-python"></a>

The following Python program detects the sentiment of input text\. You must specify the language of the input text\.

```
import boto3
import json

comprehend = boto3.client(service_name='comprehend', region_name='region')
                
text = "It is raining today in Seattle"

print('Calling DetectSentiment')
print(json.dumps(comprehend.detect_sentiment(Text=text, LanguageCode='en'), sort_keys=True, indent=4))
print('End of DetectSentiment\n')
```