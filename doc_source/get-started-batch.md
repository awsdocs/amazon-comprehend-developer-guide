# Real\-time batch APIs<a name="get-started-batch"></a>

To send batches of up to 25 documents, you can use the Amazon Comprehend real\-time batch operations\. Calling a batch operation is identical to calling the single document APIs for each document in the request\. Using the batch APIs can result in better performance for your applications\. For more information, see [Multiple document synchronous processing](concepts-processing-modes.md#how-batch)\.

**Topics**
+ [Batch processing with the SDK for Java](#batch-java)
+ [Batch processing with the AWS SDK for \.NET](#batch-csharp)
+ [Batch processing with the AWS CLI](#batch-cli)

## Batch processing with the SDK for Java<a name="batch-java"></a>

The following sample program shows how to use the [BatchDetectEntities](API_BatchDetectEntities.md) operation with the SDK for Java\. The response from the server contains a [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) object for each document that was successfully processed\. If there is an error processing a document, there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

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

## Batch processing with the AWS SDK for \.NET<a name="batch-csharp"></a>

The following sample program shows how to use the [BatchDetectEntities](API_BatchDetectEntities.md) operation with the AWS SDK for \.NET\. The response from the server contains a [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) object for each document that was successfully processed\. If there is an error processing a document, there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

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

## Batch processing with the AWS CLI<a name="batch-cli"></a>

These examples show how to use the batch API operations using the AWS Command Line Interface\. All of the operations except `BatchDetectDominantLanguage` use the following JSON file called `process.json` as input\. For that operation the `LanguageCode` entity is not included\.

The third document in the JSON file \(`"$$$$$$$$"`\) will cause an error during batch processing\. It is included so that the operations will include a [BatchItemError](API_BatchItemError.md) in the response\.

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

### Detect the dominant language using a batch \(AWS CLI\)<a name="batch-dominant-language"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) operation determines the dominant language of each document in a batch\. For a list of the languages that Amazon Comprehend can detect, see [Dominant language](how-languages.md)\. The following AWS CLI command calls the `BatchDetectDominantLanguage` operation\.

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

### Detect entities using a batch \(AWS CLI\)<a name="batch-entities"></a>

Use the [BatchDetectEntities](API_BatchDetectEntities.md) operation to find the entities present in a batch of documents\. For more information about entities, see [Entities](how-entities.md)\. The following AWS CLI command calls the `BatchDetectEntities` operation\.

```
aws comprehend batch-detect-entities \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```

### Detect key phrases using a batch \(AWS CLI\)<a name="batch-key-phrase"></a>

The [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md) operation returns the key noun phrases in a batch of documents\. The following AWS CLI command calls the `BatchDetectKeyNounPhrases` operation\.

```
aws comprehend batch-detect-key-phrases
    --endpoint endpoint
    --region region
    --cli-input-json file://path to input file/process.json
```

### Detect sentiment using a batch \(AWS CLI\)<a name="batch-sentiment"></a>

Detect the overall sentiment of a batch of documents using the [BatchDetectSentiment](API_BatchDetectSentiment.md) operation\. The following AWS CLI command calls the `BatchDetectSentiment` operation\.

```
aws comprehend batch-detect-sentiment \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```