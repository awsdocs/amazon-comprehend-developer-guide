# DetectEntities<a name="API_DetectEntities"></a>

Inspects text for named entities, and returns information about them\. For more information, about named entities, see [Entities](https://docs.aws.amazon.com/comprehend/latest/dg/how-entities.html) in the Comprehend Developer Guide\.

## Request Syntax<a name="API_DetectEntities_RequestSyntax"></a>

```
{
   "EndpointArn": "string",
   "LanguageCode": "string",
   "Text": "string"
}
```

## Request Parameters<a name="API_DetectEntities_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [EndpointArn](#API_DetectEntities_RequestSyntax) **   <a name="comprehend-DetectEntities-request-EndpointArn"></a>
The Amazon Resource Name of an endpoint that is associated with a custom entity recognition model\. Provide an endpoint if you want to detect entities by using your own custom model instead of the default model that is used by Amazon Comprehend\.  
If you specify an endpoint, Amazon Comprehend uses the language of your custom model, and it ignores any language code that you provide in your request\.  
For information about endpoints, see [Managing endpoints](https://docs.aws.amazon.com/comprehend/latest/dg/manage-endpoints.html)\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws(-[^:]+)?:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:entity-recognizer-endpoint/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 ** [LanguageCode](#API_DetectEntities_RequestSyntax) **   <a name="comprehend-DetectEntities-request-LanguageCode"></a>
The language of the input documents\. You can specify any of the primary languages supported by Amazon Comprehend\. All documents must be in the same language\.  
If your request includes the endpoint for a custom entity recognition model, Amazon Comprehend uses the language of your custom model, and it ignores any language code that you specify here\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt | ar | hi | ja | ko | zh | zh-TW`   
Required: No

 ** [Text](#API_DetectEntities_RequestSyntax) **   <a name="comprehend-DetectEntities-request-Text"></a>
A UTF\-8 text string\. The maximum string size is 100 KB\.  
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

 ** [Entities](#API_DetectEntities_ResponseSyntax) **   <a name="comprehend-DetectEntities-response-Entities"></a>
A collection of entities identified in the input text\. For each entity, the response provides the entity text, entity type, where the entity text begins and ends, and the level of confidence that Amazon Comprehend has in the detection\.   
If your request uses a custom entity recognition model, Amazon Comprehend detects the entities that the model is trained to recognize\. Otherwise, it detects the default entity types\. For a list of default entity types, see [Entities](https://docs.aws.amazon.com/comprehend/latest/dg/how-entities.html) in the Comprehend Developer Guide\.   
Type: Array of [Entity](API_Entity.md) objects

## Errors<a name="API_DetectEntities_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 ** InternalServerException **   
An internal server error occurred\. Retry your request\.  
HTTP Status Code: 500

 ** InvalidRequestException **   
The request is invalid\.  
HTTP Status Code: 400

 ** ResourceUnavailableException **   
The specified resource is not available\. Check the resource and try your request again\.  
HTTP Status Code: 400

 ** TextSizeLimitExceededException **   
The size of the input text exceeds the limit\. Use a smaller document\.  
HTTP Status Code: 400

 ** UnsupportedLanguageException **   
Amazon Comprehend can't process the language of the input text\. For custom entity recognition APIs, only English, Spanish, French, Italian, German, or Portuguese are accepted\. For a list of supported languages, [Supported languages](https://docs.aws.amazon.com/comprehend/latest/dg/supported-languages.html) in the Comprehend Developer Guide\.   
HTTP Status Code: 400

## Examples<a name="API_DetectEntities_Examples"></a>

### Detect entities<a name="API_DetectEntities_Example_1"></a>

If the input text is "Bob ordered two sandwiches and three ice cream cones today from a store in Seattle\.", the operation returns the following:

#### <a name="w96aac57c17c92c15b3b5"></a>

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
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehend-2017-11-27/DetectEntities) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DetectEntities) 