# Determining sentiment<a name="get-started-api-sentiment"></a>

Amazon Comprehend provides the following API operations for analyzing sentiment:
+ [DetectSentiment](API_DetectSentiment.md) – Determines the overall emotional sentiment of a document\.
+ [BatchDetectSentiment](API_BatchDetectSentiment.md) – Determine the overall sentiment in up to 25 documents in a batch\. For more information, see [Real\-time batch APIs](get-started-batch.md)\.
+ [StartSentimentDetectionJob](API_StartSentimentDetectionJob.md) – Starts an asynchronous sentiment detection job for a collection of documents\.
+ [ListSentimentDetectionJobs](API_ListSentimentDetectionJobs.md) – Returns the list of sentiment detection jobs that you have submitted\.
+ [DescribeSentimentDetectionJob](API_DescribeSentimentDetectionJob.md) – Gets the properties \(including status\) associated with the specified sentiment detection job\.
+ [StopSentimentDetectionJob](API_StopSentimentDetectionJob.md) – Stops the specified in\-progress sentiment job\.

**Topics**
+ [Determining sentiment using the AWS Command Line Interface](#get-started-api-sentiment-cli)
+ [Determining sentiment using the AWS SDK for Java](#get-started-api-sentiment-java)
+ [Determining sentiment using the AWS SDK for Python \(Boto\)](#get-started-api-sentiment-python)
+ [Determining sentiment using the AWS SDK for \.NET](#get-started-api-sentiment-c-sharp)

## Determining sentiment using the AWS Command Line Interface<a name="get-started-api-sentiment-cli"></a>

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

## Determining sentiment using the AWS SDK for Java<a name="get-started-api-sentiment-java"></a>

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

## Determining sentiment using the AWS SDK for Python \(Boto\)<a name="get-started-api-sentiment-python"></a>

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

## Determining sentiment using the AWS SDK for \.NET<a name="get-started-api-sentiment-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

The \.NET example in this section uses the AWS SDK for \.NET\. 

```
using System;
using Amazon.Comprehend;
using Amazon.Comprehend.Model;

namespace Comprehend
{
    class Program
    {
        static void Main(string[] args)
        {
            String text = "It is raining today in Seattle";

            AmazonComprehendClient comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.USWest2);

            // Call DetectKeyPhrases API
            Console.WriteLine("Calling DetectSentiment");
            DetectSentimentRequest detectSentimentRequest = new DetectSentimentRequest()
            {
                Text = text,
                LanguageCode = "en"
            };
            DetectSentimentResponse detectSentimentResponse = comprehendClient.DetectSentiment(detectSentimentRequest);
            Console.WriteLine(detectSentimentResponse.Sentiment);
            Console.WriteLine("Done");
        }
    }
}
```