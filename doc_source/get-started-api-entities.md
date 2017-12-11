# Detecting Named Entities<a name="get-started-api-entities"></a>

To determine the named entities in a document, use the Amazon Comprehend [DetectEntities](API_DetectEntities.md) operation\. To detect entities in up to 25 documents in a batch, use the [BatchDetectEntities](API_BatchDetectEntities.md) operation\. For more information, see [Using the Batch APIs](get-started-batch.md)\.


+ [Detecting Named Entities Using the AWS Command Line Interface](#get-started-api-entities-cli)
+ [Detecting Named Entities Using the AWS SDK for Java](#get-started-api-entities-java)
+ [Detecting Named Entities Using the AWS SDK for Python \(Boto\)](#get-started-api-entities-python)

## Detecting Named Entities Using the AWS Command Line Interface<a name="get-started-api-entities-cli"></a>

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

## Detecting Named Entities Using the AWS SDK for Java<a name="get-started-api-entities-java"></a>

The following example uses the `DetectEntities` operation with Java\. You must specify the language of the input text\.

```
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.DetectEntitiesRequest;
import com.amazonaws.services.comprehend.model.DetectEntitiesResult;

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

## Detecting Named Entities Using the AWS SDK for Python \(Boto\)<a name="get-started-api-entities-python"></a>

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