# DetectEntities<a name="API_DetectEntities"></a>

Inspects text for named entities, and returns information about them\. For more information, about named entities, see [Entities](how-entities.md)\. 

## Request Syntax<a name="API_DetectEntities_RequestSyntax"></a>

```
{
   "[LanguageCode](#comprehend-DetectEntities-request-LanguageCode)": "string",
   "[Text](#comprehend-DetectEntities-request-Text)": "string"
}
```

## Request Parameters<a name="API_DetectEntities_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [LanguageCode](#API_DetectEntities_RequestSyntax) **   <a name="comprehend-DetectEntities-request-LanguageCode"></a>
The language of the input documents\. You can specify English \("en"\) or Spanish \("es"\)\. All documents must be in the same language\.  
Type: String  
Valid Values:` en | es`   
Required: Yes

 ** [Text](#API_DetectEntities_RequestSyntax) **   <a name="comprehend-DetectEntities-request-Text"></a>
A UTF\-8 text string\. Each string must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectEntities_ResponseSyntax"></a>

```
{
   "[Entities](#comprehend-DetectEntities-response-Entities)": [ 
      { 
         "[BeginOffset](API_Entity.md#comprehend-Type-Entity-BeginOffset)": number,
         "[EndOffset](API_Entity.md#comprehend-Type-Entity-EndOffset)": number,
         "[Score](API_Entity.md#comprehend-Type-Entity-Score)": number,
         "[Text](API_Entity.md#comprehend-Type-Entity-Text)": "string",
         "[Type](API_Entity.md#comprehend-Type-Entity-Type)": "string"
      }
   ]
}
```

## Response Elements<a name="API_DetectEntities_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Entities](#API_DetectEntities_ResponseSyntax) **   <a name="comprehend-DetectEntities-response-Entities"></a>
A collection of entities identified in the input text\. For each entity, the response provides the entity text, entity type, where the entity text begins and ends, and the level of confidence that Amazon Comprehend has in the detection\. For a list of entity types, see [Entities](how-entities.md)\.   
Type: Array of [Entity](API_Entity.md) objects

## Errors<a name="API_DetectEntities_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

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
HTTP Status Code: 400

## Example<a name="API_DetectEntities_Examples"></a>

### Detect entities<a name="API_DetectEntities_Example_1"></a>

If the input text is "Bob ordered two sandwiches and three ice cream cones today from a store in Seattle\.", the operation returns the following:

#### <a name="w3ab1c21b5c41c15b3b5"></a>

```
    {
    "Entities": [
        {
            "Text": "Bob",
            "Score": 1.0,
            "Type": "PERSON",
            "BeginOffset": 0,
            "EndOffset": 3
        },
        {
            "Text": "two",
            "Score": 1.0,
            "Type": "QUANTITY",
            "BeginOffset": 12,
            "EndOffset": 15
        },
        {
            "Text": "three",
            "Score": 1.0,
            "Type": "QUANTITY",
            "BeginOffset": 32,
            "EndOffset": 37
        },
        {
            "Text": "Today",
            "Score": 1.0,
            "Type": "DATE",
            "BeginOffset": 54,
            "EndOffset": 59
        },
        {
            "Text": "Seattle",
            "Score": 1.0,
            "Type": "LOCATION",
            "BeginOffset": 76,
            "EndOffset": 83
        }
    ],
}
```

## See Also<a name="API_DetectEntities_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DetectEntities) 