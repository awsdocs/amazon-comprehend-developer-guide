# Real\-time analysis using the API<a name="using-api-sync"></a>

The following examples demonstrate how to use Amazon Comprehend API for real\-time analysis, using the AWS CLI, Java, and Python\. Use the examples to learn about the Amazon Comprehend synchronous operations and as building blocks for your own applications\.

**Topics**
+ [Detecting the dominant language](#get-started-api-dominant-language)
+ [Detecting named entities](#get-started-api-entities)
+ [Detecting key phrases](#get-started-api-key-phrases)
+ [Determining sentiment](#get-started-api-sentiment)
+ [Real\-time analysis for targeted sentiment](#get-started-api-targeted-sentiment)
+ [Detecting syntax](#get-started-api-syntax)
+ [Real\-time batch APIs](#get-started-batch)

## Detecting the dominant language<a name="get-started-api-dominant-language"></a>

To determine the dominant language used in text, use the [DetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectDominantLanguage.html) operation\. To detect the dominant language in up to 25 documents in a batch, use the [BatchDetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectDominantLanguage.html) operation\. For more information, see [Real\-time batch APIs](#get-started-batch)\.

**Topics**
+ [Detecting the dominant language using the AWS Command Line Interface](#get-started-api-dominant-language-cli)
+ [Detecting the dominant language using the AWS SDK for Java](#get-started-api-dominant-language-java)
+ [Detecting the dominant language using the AWS SDK for Python \(Boto\)](#get-started-api-dominant-language-python)
+ [Detecting the dominant language using the AWS SDK for \.NET](#get-started-api-dominant-language-c-sharp)

### Detecting the dominant language using the AWS Command Line Interface<a name="get-started-api-dominant-language-cli"></a>

The following example demonstrates using the `DetectDominantLanguage` operation with the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-dominant-language \
    --region region \
    --text "It is raining today in Seattle."
```

Amazon Comprehend responds with the following:

```
{
    "Languages": [
        {
            "LanguageCode": "en",
            "Score": 0.9793661236763
        }
    ]
}
```

### Detecting the dominant language using the AWS SDK for Java<a name="get-started-api-dominant-language-java"></a>

The following example uses the `DetectDominantLanguage` operation with Java\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectDominantLanguageRequest;
import com.amazonaws.services.comprehend.model.DetectDominantLanguageResult;

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

        // Call detectDominantLanguage API
        System.out.println("Calling DetectDominantLanguage");
        DetectDominantLanguageRequest detectDominantLanguageRequest = new DetectDominantLanguageRequest().withText(text);
        DetectDominantLanguageResult detectDominantLanguageResult = comprehendClient.detectDominantLanguage(detectDominantLanguageRequest);
        detectDominantLanguageResult.getLanguages().forEach(System.out::println);
        System.out.println("Calling DetectDominantLanguage\n");
        System.out.println("Done");
    }
}
```

### Detecting the dominant language using the AWS SDK for Python \(Boto\)<a name="get-started-api-dominant-language-python"></a>

The following example demonstrates using the `DetectDominantLanguage` operation with Python\.

```
import boto3
import json

comprehend = boto3.client(service_name='comprehend', region_name='region')
text = "It is raining today in Seattle"

print('Calling DetectDominantLanguage')
print(json.dumps(comprehend.detect_dominant_language(Text = text), sort_keys=True, indent=4))
print("End of DetectDominantLanguage\n")
```

### Detecting the dominant language using the AWS SDK for \.NET<a name="get-started-api-dominant-language-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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

            // Call DetectDominantLanguage API
            Console.WriteLine("Calling DetectDominantLanguage\n");
            DetectDominantLanguageRequest detectDominantLanguageRequest = new DetectDominantLanguageRequest()
            {
                Text = text
            };
            DetectDominantLanguageResponse detectDominantLanguageResponse = comprehendClient.DetectDominantLanguage(detectDominantLanguageRequest);
            foreach (DominantLanguage dl in detectDominantLanguageResponse.Languages)
                Console.WriteLine("Language Code: {0}, Score: {1}", dl.LanguageCode, dl.Score);
            Console.WriteLine("Done");
        }
    }
}
```

## Detecting named entities<a name="get-started-api-entities"></a>

To determine the named entities in a document, use the [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) operation\. To detect entities in up to 25 documents in a batch, use the [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html) operation\. For more information, see [Real\-time batch APIs](#get-started-batch)\.

**Topics**
+ [Detecting named entities using the AWS Command Line Interface](#get-started-api-entities-cli)
+ [Detecting named entities using the AWS SDK for Java](#get-started-api-entities-java)
+ [Detecting named entities using the AWS SDK for Python \(Boto\)](#get-started-api-entities-python)
+ [Detecting entities using the AWS SDK for \.NET](#get-started-api-entities-c-sharp)

### Detecting named entities using the AWS Command Line Interface<a name="get-started-api-entities-cli"></a>

The following example demonstrates using the `DetectEntities` operation using the AWS CLI\. You must specify the language of the input text\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-entities \
    --region region \
    --language-code "en" \
    --text "It is raining today in Seattle."
```

Amazon Comprehend responds with the following:

```
{
    "Entities": [
        {
            "Text": "today",
            "Score": 0.97,
            "Type": "DATE",
            "BeginOffset": 14,
            "EndOffset": 19
        },
        {
            "Text": "Seattle",
            "Score": 0.95,
            "Type": "LOCATION",
            "BeginOffset": 23,
            "EndOffset": 30
        }
    ],
    "LanguageCode": "en"
}
```

### Detecting named entities using the AWS SDK for Java<a name="get-started-api-entities-java"></a>

The following example uses the `DetectEntities` operation with Java\. You must specify the language of the input text\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectEntitiesRequest;
import com.amazonaws.services.comprehend.model.DetectEntitiesResult;

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

        // Call detectEntities API
        System.out.println("Calling DetectEntities");
        DetectEntitiesRequest detectEntitiesRequest = new DetectEntitiesRequest().withText(text)
                                                                                 .withLanguageCode("en");
        DetectEntitiesResult detectEntitiesResult  = comprehendClient.detectEntities(detectEntitiesRequest);
        detectEntitiesResult.getEntities().forEach(System.out::println);
        System.out.println("End of DetectEntities\n");
    }
}
```

### Detecting named entities using the AWS SDK for Python \(Boto\)<a name="get-started-api-entities-python"></a>

The following example uses the `DetectEntities` operation with Python\. You must specify the language of the input text\.

```
import boto3
import json

comprehend = boto3.client(service_name='comprehend', region_name='region')
text = "It is raining today in Seattle"

print('Calling DetectEntities')
print(json.dumps(comprehend.detect_entities(Text=text, LanguageCode='en'), sort_keys=True, indent=4))
print('End of DetectEntities\n')
```

### Detecting entities using the AWS SDK for \.NET<a name="get-started-api-entities-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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

            // Call DetectEntities API
            Console.WriteLine("Calling DetectEntities\n");
            DetectEntitiesRequest detectEntitiesRequest =  new DetectEntitiesRequest()
            {
                Text = text,
                LanguageCode = "en"
            };
            DetectEntitiesResponse detectEntitiesResponse = comprehendClient.DetectEntities(detectEntitiesRequest);
            foreach (Entity e in detectEntitiesResponse.Entities)
                Console.WriteLine("Text: {0}, Type: {1}, Score: {2}, BeginOffset: {3}, EndOffset: {4}",
                    e.Text, e.Type, e.Score, e.BeginOffset, e.EndOffset);
            Console.WriteLine("Done");
        }
    }
}
```

## Detecting key phrases<a name="get-started-api-key-phrases"></a>

To determine the key noun phrases used in text, use the [DetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectKeyPhrases.html) operation\. To detect the key noun phrases in up to 25 documents in a batch, use the [BatchDetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectKeyPhrases.html) operation\. For more information, see [Real\-time batch APIs](#get-started-batch)\.

**Topics**
+ [Detecting key phrases using the AWS Command Line Interface](#get-started-api-key-phrases-cli)
+ [Detecting key phrases using the AWS SDK for Java](#get-started-api-key-phrases-java)
+ [Detecting key phrases using the AWS SDK for Python \(Boto\)](#get-started-api-key-phrases-python)
+ [Detecting key phrases using the AWS SDK for \.NET](#get-started-api-phrases-c-sharp)

### Detecting key phrases using the AWS Command Line Interface<a name="get-started-api-key-phrases-cli"></a>

The following example demonstrates using the `DetectKeyPhrases` operation with the AWS CLI\. You must specify the language of the input text\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-key-phrases \
    --region region \
    --language-code "en" \
    --text "It is raining today in Seattle."
```

Amazon Comprehend responds with the following:

```
{
    "LanguageCode": "en",
    "KeyPhrases": [
        {
            "Text": "today",
            "Score": 0.89,
            "BeginOffset": 14,
            "EndOffset": 19
        },
        {
            "Text": "Seattle",
            "Score": 0.91,
            "BeginOffset": 23,
            "EndOffset": 30
        }
    ]
}
```

### Detecting key phrases using the AWS SDK for Java<a name="get-started-api-key-phrases-java"></a>

The following example uses the `DetectKeyPhrases` operation with Java\. You must specify the language of the input text\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectKeyPhrasesRequest;
import com.amazonaws.services.comprehend.model.DetectKeyPhrasesResult;

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

        // Call detectKeyPhrases API
        System.out.println("Calling DetectKeyPhrases");
        DetectKeyPhrasesRequest detectKeyPhrasesRequest = new DetectKeyPhrasesRequest().withText(text)
                                                                                       .withLanguageCode("en");
        DetectKeyPhrasesResult detectKeyPhrasesResult = comprehendClient.detectKeyPhrases(detectKeyPhrasesRequest);
        detectKeyPhrasesResult.getKeyPhrases().forEach(System.out::println);
        System.out.println("End of DetectKeyPhrases\n");
    }
}
```

### Detecting key phrases using the AWS SDK for Python \(Boto\)<a name="get-started-api-key-phrases-python"></a>

The following example uses the `DetectKeyPhrases` operation with Python\. You must specify the language of the input text\.

```
import boto3
import json

comprehend = boto3.client(service_name='comprehend', region_name='region')

text = "It is raining today in Seattle"

print('Calling DetectKeyPhrases')
print(json.dumps(comprehend.detect_key_phrases(Text=text, LanguageCode='en'), sort_keys=True, indent=4))
print('End of DetectKeyPhrases\n')
```

### Detecting key phrases using the AWS SDK for \.NET<a name="get-started-api-phrases-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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
            Console.WriteLine("Calling DetectKeyPhrases");
            DetectKeyPhrasesRequest detectKeyPhrasesRequest = new DetectKeyPhrasesRequest()
            {
                Text = text,
                LanguageCode = "en"
            };
            DetectKeyPhrasesResponse detectKeyPhrasesResponse = comprehendClient.DetectKeyPhrases(detectKeyPhrasesRequest);
            foreach (KeyPhrase kp in detectKeyPhrasesResponse.KeyPhrases)
                Console.WriteLine("Text: {1}, Type: {1}, BeginOffset: {2}, EndOffset: {3}",
                    kp.Text, kp.Text, kp.BeginOffset, kp.EndOffset);
            Console.WriteLine("Done");
        }
    }
}
```

## Determining sentiment<a name="get-started-api-sentiment"></a>

Amazon Comprehend provides the following API operations for analyzing sentiment:
+ [DetectSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectSentiment.html) – Determines the overall emotional sentiment of a document\.
+  [BatchDetectSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectSentiment.html) – Determine the overall sentiment in up to 25 documents in a batch\. For more information, see [Real\-time batch APIs](#get-started-batch)
+  [StartSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartSentimentDetectionJob.html) – Starts an asynchronous sentiment detection job for a collection of documents\.
+  [ListSentimentDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ListSentimentDetectionJobs.html) – Returns the list of sentiment detection jobs that you have submitted\.
+  [DescribeSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeSentimentDetectionJob.html) – Gets the properties \(including status\) associated with the specified sentiment detection job\.
+  [StopSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StopSentimentDetectionJob.html) – Stops the specified in\-progress sentiment job\.

**Topics**
+ [Determining sentiment using the AWS Command Line Interface](#get-started-api-sentiment-cli)
+ [Determining sentiment using the AWS SDK for Java](#get-started-api-sentiment-java)
+ [Determining sentiment using the AWS SDK for Python \(Boto\)](#get-started-api-sentiment-python)
+ [Determining sentiment using the AWS SDK for \.NET](#get-started-api-sentiment-c-sharp)

### Determining sentiment using the AWS Command Line Interface<a name="get-started-api-sentiment-cli"></a>

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

### Determining sentiment using the AWS SDK for Java<a name="get-started-api-sentiment-java"></a>

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

### Determining sentiment using the AWS SDK for Python \(Boto\)<a name="get-started-api-sentiment-python"></a>

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

### Determining sentiment using the AWS SDK for \.NET<a name="get-started-api-sentiment-c-sharp"></a>

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

## Real\-time analysis for targeted sentiment<a name="get-started-api-targeted-sentiment"></a>

Amazon Comprehend provides the following API operations for targeted sentiment real\-time analysis:
+ [DetectTargetedSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectTargetedSentiment.html) – Analyzes sentiment of the entities mentioned in a document\.
+  [BatchDetectTargetedSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectTargetedSentiment.html) – Analyzes targeted sentiment for up to 25 documents in a batch\. For more information, see [Real\-time batch APIs](#get-started-batch)

If the text you are analyzing doesn't include any targeted sentiment [Entity types](how-targeted-sentiment.md#how-targeted-sentiment-entities), the API returns an empty Entities array\.

### Analyzing targeted sentiment using the AWS Command Line Interface<a name="get-started-api-targeted-sentiment-cli"></a>

The following example demonstrates using the `DetectTargetedSentiment` operation with the AWS CLI\. This example specifies the language of the input text\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend detect-targeted-sentiment \
    --region region \
    --language-code "en" \
    --text "The burger was cooked perfectly but it was cold. The service was OK."
```

 Amazon Comprehend responds with the following:

```
{
"Entities": [
    {
      "DescriptiveMentionIndex": [
        0
      ],
      "Mentions": [
        {
          "BeginOffset": 4,
          "EndOffset": 10,
          "Score": 1,
          "GroupScore": 1,
          "Text": "burger",
          "Type": "OTHER",
          "MentionSentiment": {
            "Sentiment": "POSITIVE",
            "SentimentScore": {
              "Mixed": 0.001515,
              "Negative": 0.000822,
              "Neutral": 0.000243,
              "Positive": 0.99742
            }
          }
        },
        {
          "BeginOffset": 36,
          "EndOffset": 38,
          "Score": 0.999843,
          "GroupScore": 0.999661,
          "Text": "it",
          "Type": "OTHER",
          "MentionSentiment": {
            "Sentiment": "NEGATIVE",
            "SentimentScore": {
              "Mixed": 0,
              "Negative": 0.999996,
              "Neutral": 0.000004,
              "Positive": 0
            }
          }
        }
      ]
    },
    {
      "DescriptiveMentionIndex": [
        0
      ],
      "Mentions": [
        {
          "BeginOffset": 53,
          "EndOffset": 60,
          "Score": 1,
          "GroupScore": 1,
          "Text": "service",
          "Type": "ATTRIBUTE",
          "MentionSentiment": {
            "Sentiment": "NEUTRAL",
            "SentimentScore": {
              "Mixed": 0.000033,
              "Negative": 0.000089,
              "Neutral": 0.993325,
              "Positive": 0.006553
            }
          }
        }
      ]
    }
  ]
}
```

## Detecting syntax<a name="get-started-api-syntax"></a>

To parse text to extract the individual words and determine the parts of speech for each word, use the [DetectSyntax](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectSyntax.html) operation\. To parse the syntax of up to 25 documents in a batch, use the [BatchDetectSyntax](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectSyntax.html) operation\. For more information, see [Real\-time batch APIs](#get-started-batch)\.

**Topics**
+ [Detecting syntax using the AWS Command Line Interface\.](#get-started-api-syntax-cli)
+ [Detecting syntax using the AWS SDK for Java](#get-started-api-syntax-java)
+ [Detecting parts of speech using the AWS SDK for Python \(Boto\)](#get-started-api-pos-python)
+ [Detecting syntax using the AWS SDK for \.NET](#get-started-api-syntax-c-sharp)

### Detecting syntax using the AWS Command Line Interface\.<a name="get-started-api-syntax-cli"></a>

The following example demonstrates using the `DetectSyntax` operation with the AWS CLI\. This example specifies the language of the input text\. 

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. 

```
aws comprehend detect-syntax \
   --region region \
   --language-code "en" \
   --text "It is raining today in Seattle."
```

Amazon Comprehend responds with the following:

```
{
    "SyntaxTokens": [
        {
            "Text": "It",
            "EndOffset": 2,
            "BeginOffset": 0,
            "PartOfSpeech": {
                "Tag": "PRON",
                "Score": 0.8389829397201538
            },
            "TokenId": 1
        },
        {
            "Text": "is",
            "EndOffset": 5,
            "BeginOffset": 3,
            "PartOfSpeech": {
                "Tag": "AUX",
                "Score": 0.9189288020133972
            },
            "TokenId": 2
        },
        {
            "Text": "raining",
            "EndOffset": 13,
            "BeginOffset": 6,
            "PartOfSpeech": {
                "Tag": "VERB",
                "Score": 0.9977611303329468
            },
            "TokenId": 3
        },
        {
            "Text": "today",
            "EndOffset": 19,
            "BeginOffset": 14,
            "PartOfSpeech": {
                "Tag": "NOUN",
                "Score": 0.9993606209754944
            },
            "TokenId": 4
        },
        {
            "Text": "in",
            "EndOffset": 22,
            "BeginOffset": 20,
            "PartOfSpeech": {
                "Tag": "ADP",
                "Score": 0.9999061822891235
            },
            "TokenId": 5
        },
        {
            "Text": "Seattle",
            "EndOffset": 30,
            "BeginOffset": 23,
            "PartOfSpeech": {
                "Tag": "PROPN",
                "Score": 0.9940338730812073
            },
            "TokenId": 6
        },
        {
            "Text": ".",
            "EndOffset": 31,
            "BeginOffset": 30,
            "PartOfSpeech": {
                "Tag": "PUNCT",
                "Score": 0.9999997615814209
            },
            "TokenId": 7
        }
    ]
}
```

### Detecting syntax using the AWS SDK for Java<a name="get-started-api-syntax-java"></a>

The following Java program detects the syntax of the input text\. You must specify the language of the input text\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectSyntaxRequest;
import com.amazonaws.services.comprehend.model.DetectSyntaxResult;

public class App
{
	public static void main( String[] args )
	{

		String text = "It is raining today in Seattle.";
		String region = "region"

		// Create credentials using a provider chain. For more information, see
		// https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
		AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();

		AmazonComprehend comprehendClient =
				AmazonComprehendClientBuilder.standard()
						.withCredentials(awsCreds)
						.withRegion(region)
						.build();

		// Call detectSyntax API
		System.out.println("Calling DetectSyntax");
		DetectSyntaxRequest detectSyntaxRequest = new DetectSyntaxRequest()
				.withText(text)
				.withLanguageCode("en");
		DetectSyntaxResult detectSyntaxResult = comprehendClient.detectSyntax(detectSyntaxRequest);
		detectSyntaxResult.getSyntaxTokens().forEach(System.out::println);
		System.out.println("End of DetectSyntax\n");
		System.out.println( "Done" );
	}
}
```

### Detecting parts of speech using the AWS SDK for Python \(Boto\)<a name="get-started-api-pos-python"></a>

The following Python program detects the parts of speech in the input text\. You must specify the language of the input text\.

```
import boto3
import json

comprehend = boto3.client(service_name='comprehend', region_name='region')
text = "It is raining today in Seattle"

print('Calling DetectSyntax')
print(json.dumps(comprehend.detect_syntax(Text=text, LanguageCode='en'), sort_keys=True, indent=4))
print('End of DetectSyntax\n')
```

### Detecting syntax using the AWS SDK for \.NET<a name="get-started-api-syntax-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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

			AmazonComprehendClient comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.region);

			// Call DetectSyntax API
			Console.WriteLine("Calling DetectSyntax\n");
			DetectSyntaxRequest detectSyntaxRequest =  new DetectSyntaxRequest()
			{
				Text = text,
				LanguageCode = "en"
			};
			DetectSyntaxResponse detectSyntaxResponse = comprehendClient.DetectSyntax(detectSyntaxRequest);
			foreach (SyntaxToken s in detectSyntaxResponse.SyntaxTokens)
			Console.WriteLine("Text: {0}, PartOfSpeech: {1}, Score: {2}, BeginOffset: {3}, EndOffset: {4}",
					e.Text, e.PartOfSpeech, e.Score, e.BeginOffset, e.EndOffset);
			Console.WriteLine("Done");
		}
	}
}
```

## Real\-time batch APIs<a name="get-started-batch"></a>

To send batches of up to 25 documents, you can use the Amazon Comprehend real\-time batch operations\. Calling a batch operation is identical to calling the single document APIs for each document in the request\. Using the batch APIs can result in better performance for your applications\. For more information, see [Multiple document synchronous processing](concepts-processing-modes.md#how-batch)\.

**Topics**
+ [Batch processing with the SDK for Java](#batch-java)
+ [Batch processing with the AWS SDK for \.NET](#batch-csharp)
+ [Batch processing with the AWS CLI](#batch-cli)

### Batch processing with the SDK for Java<a name="batch-java"></a>

The following sample program shows how to use the [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html) operation with the SDK for Java\. The response from the server contains a [BatchDetectEntitiesItemResult](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntitiesItemResult.html) object for each document that was successfully processed\. If there is an error processing a document, there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

```
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.BatchDetectEntitiesItemResult;
import com.amazonaws.services.comprehend.model.BatchDetectEntitiesRequest;
import com.amazonaws.services.comprehend.model.BatchDetectEntitiesResult;
import com.amazonaws.services.comprehend.model.BatchItemError;

public class App
{
    public static void main( String[] args )
    {

        // Create credentials using a provider chain. For more information, see
        // https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
        AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();

        AmazonComprehend comprehendClient =
            AmazonComprehendClientBuilder.standard()
                                         .withCredentials(awsCreds)
                                         .withRegion("region")
                                         .build();

        String[] textList = {"I love Seattle", "Today is Sunday", "Tomorrow is Monday", "I love Seattle"};

        // Call detectEntities API
        System.out.println("Calling BatchDetectEntities");
        BatchDetectEntitiesRequest batchDetectEntitiesRequest = new BatchDetectEntitiesRequest().withTextList(textList)
                                                                                                .withLanguageCode("en");
        BatchDetectEntitiesResult batchDetectEntitiesResult  = client.batchDetectEntities(batchDetectEntitiesRequest);

        for(BatchDetectEntitiesItemResult item : batchDetectEntitiesResult.getResultList()) {
            System.out.println(item);
        }

        // check if we need to retry failed requests
        if (batchDetectEntitiesResult.getErrorList().size() != 0)
        {
            System.out.println("Retrying Failed Requests");
            ArrayList<String> textToRetry = new ArrayList<String>();
            for(BatchItemError errorItem : batchDetectEntitiesResult.getErrorList())
            {
                textToRetry.add(textList[errorItem.getIndex()]);
            }

            batchDetectEntitiesRequest = new BatchDetectEntitiesRequest().withTextList(textToRetry).withLanguageCode("en");
            batchDetectEntitiesResult  = client.batchDetectEntities(batchDetectEntitiesRequest);

            for(BatchDetectEntitiesItemResult item : batchDetectEntitiesResult.getResultList()) {
                System.out.println(item);
            }

        }
        System.out.println("End of DetectEntities");
    }
}
```

### Batch processing with the AWS SDK for \.NET<a name="batch-csharp"></a>

The following sample program shows how to use the [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html) operation with the AWS SDK for \.NET\. The response from the server contains a [BatchDetectEntitiesItemResult](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntitiesItemResult.html) object for each document that was successfully processed\. If there is an error processing a document, there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS guide for \.NET developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

```
using System;
using System.Collections.Generic;
using Amazon.Comprehend;
using Amazon.Comprehend.Model;

namespace Comprehend
{
    class Program
    {
        // Helper method for printing properties
        static private void PrintEntity(Entity entity)
        {
            Console.WriteLine("     Text: {0}, Type: {1}, Score: {2}, BeginOffset: {3} EndOffset: {4}",
                entity.Text, entity.Type, entity.Score, entity.BeginOffset, entity.EndOffset);
        }

        static void Main(string[] args)
        {
            AmazonComprehendClient comprehendClient = new AmazonComprehendClient(Amazon.RegionEndpoint.USWest2);

            List<String> textList = new List<String>()
            {
                { "I love Seattle" },
                { "Today is Sunday" },
                { "Tomorrow is Monday" },
                { "I love Seattle" }
            };

            // Call detectEntities API
            Console.WriteLine("Calling BatchDetectEntities");
            BatchDetectEntitiesRequest batchDetectEntitiesRequest = new BatchDetectEntitiesRequest()
            {
                TextList = textList,
                LanguageCode = "en"
            };
            BatchDetectEntitiesResponse batchDetectEntitiesResponse = comprehendClient.BatchDetectEntities(batchDetectEntitiesRequest);

            foreach (BatchDetectEntitiesItemResult item in batchDetectEntitiesResponse.ResultList)
            {
                Console.WriteLine("Entities in {0}:", textList[item.Index]);
                foreach (Entity entity in item.Entities)
                    PrintEntity(entity);
            }

            // check if we need to retry failed requests
            if (batchDetectEntitiesResponse.ErrorList.Count != 0)
            {
                Console.WriteLine("Retrying Failed Requests");
                List<String> textToRetry = new List<String>();
                foreach(BatchItemError errorItem in batchDetectEntitiesResponse.ErrorList)
                    textToRetry.Add(textList[errorItem.Index]);

                batchDetectEntitiesRequest = new BatchDetectEntitiesRequest()
                {
                    TextList = textToRetry,
                    LanguageCode = "en"
                };

                batchDetectEntitiesResponse = comprehendClient.BatchDetectEntities(batchDetectEntitiesRequest);

                foreach(BatchDetectEntitiesItemResult item in batchDetectEntitiesResponse.ResultList)
                {
                    Console.WriteLine("Entities in {0}:", textList[item.Index]);
                    foreach (Entity entity in item.Entities)
                        PrintEntity(entity);
                }
            }
            Console.WriteLine("End of DetectEntities");
        }
    }
}
```

### Batch processing with the AWS CLI<a name="batch-cli"></a>

These examples show how to use the batch API operations using the AWS Command Line Interface\. All of the operations except `BatchDetectDominantLanguage` use the following JSON file called `process.json` as input\. For that operation the `LanguageCode` entity is not included\.

The third document in the JSON file \(`"$$$$$$$$"`\) will cause an error during batch processing\. It is included so that the operations will include an [BatchItemError](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchItemError.html) in the response\.

```
{
   "LanguageCode": "en",
   "TextList": [
      "I have been living in Seattle for almost 4 years",
      "It is raining today in Seattle",
      "$$$$$$$$"
   ]
}
```

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

**Topics**
+ [Detect the dominant language using a batch \(AWS CLI\)](#batch-dominant-language)
+ [Detect entities using a batch \(AWS CLI\)](#batch-entities)
+ [Detect key phrases using a batch \(AWS CLI\)](#batch-key-phrase)
+ [Detect sentiment using a batch \(AWS CLI\)](#batch-sentiment)

#### Detect the dominant language using a batch \(AWS CLI\)<a name="batch-dominant-language"></a>

The [BatchDetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectDominantLanguage.html) operation determines the dominant language of each document in a batch\. For a list of the languages that Amazon Comprehend can detect, see [Dominant language](how-languages.md)\. The following AWS CLI command calls the `BatchDetectDominantLanguage` operation\.

```
aws comprehend batch-detect-dominant-language \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```

The following is the response from the `BatchDetectDominantLanguage` operation:

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
          "Index": 1
          "Languages":[
            {
              "LanguageCode":"en",
              "Score": 0.82
            }
          ]
        }
    ],
    "ErrorList": [
      {
        "Index": 2,
        "ErrorCode": "InternalServerException",
        "ErrorMessage": "Unexpected Server Error. Please try again."
      }
    ]
}
```

#### Detect entities using a batch \(AWS CLI\)<a name="batch-entities"></a>

Use the [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html) operation to find the entities present in a batch of documents\. For more information about entities, see [Entities](how-entities.md)\. The following AWS CLI command calls the `BatchDetectEntities` operation\.

```
aws comprehend batch-detect-entities \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```

#### Detect key phrases using a batch \(AWS CLI\)<a name="batch-key-phrase"></a>

The [BatchDetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectKeyPhrases.html) operation returns the key noun phrases in a batch of documents\. The following AWS CLI command calls the `BatchDetectKeyNounPhrases` operation\.

```
aws comprehend batch-detect-key-phrases
    --endpoint endpoint
    --region region
    --cli-input-json file://path to input file/process.json
```

#### Detect sentiment using a batch \(AWS CLI\)<a name="batch-sentiment"></a>

Detect the overall sentiment of a batch of documents using the [BatchDetectSentiment](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectSentiment.html) operation\. The following AWS CLI command calls the `BatchDetectSentiment` operation\.

```
aws comprehend batch-detect-sentiment \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```