# Using the Batch APIs<a name="get-started-batch"></a>

To send batches of up to 25 documents, you can use the Amazon Comprehend batch operations\. Calling a batch operation is identical to calling the single document APIs for each document in the request\. Using the batch APIs can result in better performance for your applications\. For more information, see [Multiple Document Synchronous Processing](how-batch.md)\.

**Topics**
+ [Batch Processing With the SDK for Java](#batch-java)
+ [Batch Processing With the AWS SDK for \.NET](#batch-csharp)
+ [Batch Processing With the AWS CLI](#batch-cli)

## Batch Processing With the SDK for Java<a name="batch-java"></a>

The following sample program shows how to use the [ BatchDetectEntities APIrequestsBatchDetectEntities  Inspects the text of a batch of documents for named entities and returns information about them\. For more information about named entities, see [Entities](how-entities.md)   Request Syntax  

```
{
   "[LanguageCode](#comprehend-BatchDetectEntities-request-LanguageCode)": "string",
   "[TextList](#comprehend-BatchDetectEntities-request-TextList)": [ "string" ]
}
```   Request Parameters  For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\. The request accepts the following data in JSON format\.  

 ** [LanguageCode](#API_BatchDetectEntities_RequestSyntax) **   <a name="comprehend-BatchDetectEntities-request-LanguageCode"></a>
The language of the input documents\. You can specify English \("en"\) or Spanish \("es"\)\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es`   
Required: Yes 

 ** [TextList](#API_BatchDetectEntities_RequestSyntax) **   <a name="comprehend-BatchDetectEntities-request-TextList"></a>
A list containing the text of the input documents\. The list can contain a maximum of 25 documents\. Each document must contain fewer than 5,000 bytes of UTF\-8 encoded characters\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\.  
Required: Yes    Response Syntax  

```
{
   "[ErrorList](#comprehend-BatchDetectEntities-response-ErrorList)": [ 
      { 
         "[ErrorCode](API_BatchItemError.md#comprehend-Type-BatchItemError-ErrorCode)": "string",
         "[ErrorMessage](API_BatchItemError.md#comprehend-Type-BatchItemError-ErrorMessage)": "string",
         "[Index](API_BatchItemError.md#comprehend-Type-BatchItemError-Index)": number
      }
   ],
   "[ResultList](#comprehend-BatchDetectEntities-response-ResultList)": [ 
      { 
         "[Entities](API_BatchDetectEntitiesItemResult.md#comprehend-Type-BatchDetectEntitiesItemResult-Entities)": [ 
            { 
               "[BeginOffset](API_Entity.md#comprehend-Type-Entity-BeginOffset)": number,
               "[EndOffset](API_Entity.md#comprehend-Type-Entity-EndOffset)": number,
               "[Score](API_Entity.md#comprehend-Type-Entity-Score)": number,
               "[Text](API_Entity.md#comprehend-Type-Entity-Text)": "string",
               "[Type](API_Entity.md#comprehend-Type-Entity-Type)": "string"
            }
         ],
         "[Index](API_BatchDetectEntitiesItemResult.md#comprehend-Type-BatchDetectEntitiesItemResult-Index)": number
      }
   ]
}
```   Response Elements  If the action is successful, the service sends back an HTTP 200 response\. The following data is returned in JSON format by the service\.  

 ** [ErrorList](#API_BatchDetectEntities_ResponseSyntax) **   <a name="comprehend-BatchDetectEntities-response-ErrorList"></a>
A list containing one [BatchItemError](API_BatchItemError.md) object for each document that contained an error\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If there are no errors in the batch, the `ErrorList` is empty\.  
Type: Array of [BatchItemError](API_BatchItemError.md) objects 

 ** [ResultList](#API_BatchDetectEntities_ResponseSyntax) **   <a name="comprehend-BatchDetectEntities-response-ResultList"></a>
A list of [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) objects containing the results of the operation\. The results are sorted in ascending order by the `Index` field and match the order of the documents in the input list\. If all of the documents contain an error, the `ResultList` is empty\.  
Type: Array of [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) objects    Errors  For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.  

 **BatchSizeLimitExceededException**   
The number of documents in the request exceeds the limit of 25\. Try your request again with fewer documents\.  
HTTP Status Code: 400 

 **InternalServerException**   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500 

 **InvalidRequestException**   
The request is invalid\.  
HTTP Status Code: 400 

 **TextSizeLimitExceededException**   
The size of the input text exceeds the limit\. Use a smaller document\.  
HTTP Status Code: 400 

 **UnsupportedLanguageException**   
Amazon Comprehend can't process the language of the input text\. For all APIs except `DetectDominantLanguage`, Amazon Comprehend accepts only English or Spanish text\. For the `DetectDominantLanguage` API, Amazon Comprehend detects 100 languages\. For a list of languages, see [Dominant Language](how-languages.md)   
HTTP Status Code: 400    See Also   For more information about using this API in one of the language\-specific AWS SDKs, see the following:    [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/BatchDetectEntities)     [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/BatchDetectEntities)    ](API_BatchDetectEntities.md) operation with the SDK for Java\. The response from the server contains a [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) object for each document that was successfully processed\. If there is an error processing a document there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

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

## Batch Processing With the AWS SDK for \.NET<a name="batch-csharp"></a>

The following sample program shows how to use the [BatchDetectEntities](API_BatchDetectEntities.md) operation with the AWS SDK for \.NET\. The response from the server contains a [BatchDetectEntitiesItemResult](API_BatchDetectEntitiesItemResult.md) object for each document that was successfully processed\. If there is an error processing a document there will be a record in the error list in the response\. The example gets each of the documents with an error and resends them\.

The \.NET example in this section uses the [AWS SDK for \.NET](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. You can use the [AWS Toolkit for Visual Studio](http://docs.aws.amazon.com/AWSToolkitVS/latest/UserGuide/welcome.html) to develop AWS applications using \.NET\. It includes helpful templates and the AWS Explorer for deploying applications and managing services\. For a \.NET developer perspective of AWS, see the [AWS Guide for \.NET Developers](http://docs.aws.amazon.com/sdk-for-net/latest/developer-guide/welcome.html)\. 

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

## Batch Processing With the AWS CLI<a name="batch-cli"></a>

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
+ [Detect the Dominant Language Using a Batch \(AWS CLI\)](#batch-dominant-language)
+ [Detect Entities Using a Batch \(AWS CLI\)](#batch-entities)
+ [Detect Key Phrases Using a Batch \(AWS CLI\)](#batch-key-phrase)
+ [Detect Sentiment Using a Batch \(AWS CLI\)](#batch-sentiment)

### Detect the Dominant Language Using a Batch \(AWS CLI\)<a name="batch-dominant-language"></a>

The [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md) operation determines the dominant language of each document in a batch\. For a list of the languages that Amazon Comprehend can detect, see [Dominant Language](how-languages.md)\. The following AWS CLI command calls the `BatchDetectDominantLanguage` operation\.

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

### Detect Entities Using a Batch \(AWS CLI\)<a name="batch-entities"></a>

Use the [BatchDetectEntities](API_BatchDetectEntities.md) operation to find the entities present in a batch of documents\. For more information about entities, see [Entities](how-entities.md)\. The following AWS CLI command calls the `BatchDetectEntities` operation\.

```
aws comprehend batch-detect-entities \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```

### Detect Key Phrases Using a Batch \(AWS CLI\)<a name="batch-key-phrase"></a>

The [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md) operation returns the key noun phrases in a batch of documents\. The following AWS CLI command calls the `BatchDetectKeyNounPhrases` operation\.

```
aws comprehend batch-detect-key-phrases
    --endpoint endpoint
    --region region
    --cli-input-json file://path to input file/process.json
```

### Detect Sentiment Using a Batch \(AWS CLI\)<a name="batch-sentiment"></a>

Detect the overall sentiment of a batch of documents using the [BatchDetectSentiment](API_BatchDetectSentiment.md) operation\. The following AWS CLI command calls the `BatchDetectSentiment` operation\.

```
aws comprehend batch-detect-sentiment \
    --endpoint endpoint \
    --region region \
    --cli-input-json file://path to input file/process.json
```