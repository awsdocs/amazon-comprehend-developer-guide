# Detecting Key Phrases<a name="get-started-api-key-phrases"></a>

To determine the key noun phrases used in text, use the Amazon Comprehend [ DetectKeyPhrases ](API_DetectKeyPhrases.md) operation\. To detect the key noun phrases in up to 25 documents in a batch, use the [ BatchDetectKeyPhrases ](API_BatchDetectKeyPhrases.md) operation\. For more information, see [Using the Batch APIs](get-started-batch.md)\.

**Topics**
+ [Detecting Key Phrases Using the AWS Command Line Interface](#get-started-api-key-phrases-cli)
+ [Detecting Key Phrases Using the AWS SDK for Java](#get-started-api-key-phrases-java)
+ [Detecting Key Phrases Using the AWS SDK for Python \(Boto\)](#get-started-api-key-phrases-python)
+ [Detecting Key Phrases Using the AWS SDK for \.NET](#get-started-api-phrases-c-sharp)

## Detecting Key Phrases Using the AWS Command Line Interface<a name="get-started-api-key-phrases-cli"></a>

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

## Detecting Key Phrases Using the AWS SDK for Java<a name="get-started-api-key-phrases-java"></a>

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

## Detecting Key Phrases Using the AWS SDK for Python \(Boto\)<a name="get-started-api-key-phrases-python"></a>

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

## Detecting Key Phrases Using the AWS SDK for \.NET<a name="get-started-api-phrases-c-sharp"></a>

The \.NET example in this section uses the [AWS SDK for \.NET](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](https://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS Guide for \.NET Developers](https://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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