# Detecting Key Phrases<a name="get-started-api-key-phrases"></a>

To determine the key noun phrases used in text, use the Amazon Comprehend [DetectKeyPhrases](API_DetectKeyPhrases.md) operation\. To detect the key noun phrases in up to 25 documents in a batch, use the [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md) operation\. For more information, see [Using the Batch APIs](get-started-batch.md)\.


+ [Detecting Key Phrases Using the AWS Command Line Interface](#get-started-api-key-phrases-cli)
+ [Detecting Key Phrases Using the AWS SDK for Java](#get-started-api-key-phrases-java)
+ [Detecting Key Phrases Using the AWS SDK for Python \(Boto\)](#get-started-api-key-phrases-python)

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
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectKeyPhrasesRequest;
import com.amazonaws.services.comprehend.model.DetectKeyPhrasesResult;

public class App 
{
    public static void main( String[] args )
    {

        String text = "It is raining today in Seattle";

        BasicAWSCredentials awsCreds = new BasicAWSCredentials("access key ID", "secret access key");

        AmazonComprehend comprehendClient = 
            AmazonComprehendClientBuilder.standard()
                                         .withCredentials(new AWSStaticCredentialsProvider(awsCreds))
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