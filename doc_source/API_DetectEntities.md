# DetectEntities<a name="API_DetectEntities"></a>

Inspects text for named entities, and returns information about them\. For more information, about named entities, see [Detecting Entities](how-entities.md)\. 

## Request Syntax<a name="API_DetectEntities_RequestSyntax"></a>

```
{
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_DetectEntities_RequestParameters"></a>

For information about the parameters that are common to all actions, see Common Parameters\.

The request accepts the following data in JSON format\.

 ** LanguageCode **   
The RFC 5646 language code of the input text\. If you specify a language code that the service does not support, it returns `UnsupportedLanguageException` exception\. For more information about RFC 5646, see [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646) on the *IETF Tools* web site\.   
Type: String  
Valid Values:` en | es`   
Required: Yes

 ** Text **   
A UTF\-8 text string\. Each string must contain fewer that 5,000 bytes of UTF\-8 encoded characters\.  
Type: String  
Length Constraints: Minimum length of 1\.  
Required: Yes

## Response Syntax<a name="API_DetectEntities_ResponseSyntax"></a>

```
{
   "Entities": [ 
      { 
         "BeginOffset": number,
         "EndOffset": number,
         "Score": number,
         "Text": "string",
         "Type": "string"
      }
   ]
}
```

## Response Elements<a name="API_DetectEntities_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** Entities **   
A collection of entities identified in the input text\. For each entity, the response provides the entity text, entity type, where the entity text begins and ends, and the level of confidence that Amazon Comprehend has in the detection\. For a list of entity types, see [Detecting Entities](how-entities.md)\.   
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
Amazon Comprehend can't process the language of the input text\. For all APIs except `DetectDominantLanguage`, Amazon Comprehend accepts only English or Spanish text\. For the `DetectDominantLanguage` API, Amazon Comprehend detects 100 languages\. For a list of languages, see [Detecting the Primary Language ](how-languages.md)   
HTTP Status Code: 400

## Example<a name="API_DetectEntities_Examples"></a>

### Detect entities<a name="API_DetectEntities_Example_1"></a>

If the input text is "Bob ordered two sandwiches and three ice cream cones today from a store in Seattle\.", the operation returns the following:

#### <a name="w3ab1c23b5c26c15b3b5"></a>

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

+  [AWS Command Line Interface](http://docs.aws.amazon.com/goto/aws-cli/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for \.NET](http://docs.aws.amazon.com/goto/DotNetSDKV3/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for JavaScript](http://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for PHP V3](http://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for Python](http://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectEntities) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DetectEntities) 