# DetectPHI<a name="API_medical_DetectPHI"></a>

 Inspects the clinical text for protected health information \(PHI\) entities and returns the entity category, location, and confidence score for each entity\. Amazon Comprehend Medical only detects entities in English language texts\.

## Request Syntax<a name="API_medical_DetectPHI_RequestSyntax"></a>

```
{
   "[Text](#comprehend-medical_DetectPHI-request-Text)": "string"
}
```

## Request Parameters<a name="API_medical_DetectPHI_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Text](#API_medical_DetectPHI_RequestSyntax) **   <a name="comprehend-medical_DetectPHI-request-Text"></a>
 A UTF\-8 text string containing the clinical content being examined for PHI entities\. Each string must contain fewer than 20,000 bytes of characters\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 20000\.  
Required: Yes

## Response Syntax<a name="API_medical_DetectPHI_ResponseSyntax"></a>

```
{
   "[Entities](#comprehend-medical_DetectPHI-response-Entities)": [ 
      { 
         "[Attributes](API_medical_Entity.md#comprehend-Type-medical_Entity-Attributes)": [ 
            { 
               "[BeginOffset](API_medical_Attribute.md#comprehend-Type-medical_Attribute-BeginOffset)": number,
               "[Category](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Category)": "string",
               "[EndOffset](API_medical_Attribute.md#comprehend-Type-medical_Attribute-EndOffset)": number,
               "[Id](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Id)": number,
               "[RelationshipScore](API_medical_Attribute.md#comprehend-Type-medical_Attribute-RelationshipScore)": number,
               "[RelationshipType](API_medical_Attribute.md#comprehend-Type-medical_Attribute-RelationshipType)": "string",
               "[Score](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Score)": number,
               "[Text](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Text)": "string",
               "[Traits](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Traits)": [ 
                  { 
                     "[Name](API_medical_Trait.md#comprehend-Type-medical_Trait-Name)": "string",
                     "[Score](API_medical_Trait.md#comprehend-Type-medical_Trait-Score)": number
                  }
               ],
               "[Type](API_medical_Attribute.md#comprehend-Type-medical_Attribute-Type)": "string"
            }
         ],
         "[BeginOffset](API_medical_Entity.md#comprehend-Type-medical_Entity-BeginOffset)": number,
         "[Category](API_medical_Entity.md#comprehend-Type-medical_Entity-Category)": "string",
         "[EndOffset](API_medical_Entity.md#comprehend-Type-medical_Entity-EndOffset)": number,
         "[Id](API_medical_Entity.md#comprehend-Type-medical_Entity-Id)": number,
         "[Score](API_medical_Entity.md#comprehend-Type-medical_Entity-Score)": number,
         "[Text](API_medical_Entity.md#comprehend-Type-medical_Entity-Text)": "string",
         "[Traits](API_medical_Entity.md#comprehend-Type-medical_Entity-Traits)": [ 
            { 
               "[Name](API_medical_Trait.md#comprehend-Type-medical_Trait-Name)": "string",
               "[Score](API_medical_Trait.md#comprehend-Type-medical_Trait-Score)": number
            }
         ],
         "[Type](API_medical_Entity.md#comprehend-Type-medical_Entity-Type)": "string"
      }
   ],
   "[ModelVersion](#comprehend-medical_DetectPHI-response-ModelVersion)": "string",
   "[PaginationToken](#comprehend-medical_DetectPHI-response-PaginationToken)": "string"
}
```

## Response Elements<a name="API_medical_DetectPHI_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Entities](#API_medical_DetectPHI_ResponseSyntax) **   <a name="comprehend-medical_DetectPHI-response-Entities"></a>
 The collection of PHI entities extracted from the input text and their associated information\. For each entity, the response provides the entity text, the entity category, where the entity text begins and ends, and the level of confidence that Amazon Comprehend Medical has in its detection\.   
Type: Array of [Entity](API_medical_Entity.md) objects

 ** [ModelVersion](#API_medical_DetectPHI_ResponseSyntax) **   <a name="comprehend-medical_DetectPHI-response-ModelVersion"></a>
The version of the model used to analyze the documents\. The version number looks like X\.X\.X\. You can use this information to track the model used for a particular batch of documents\.  
Type: String  
Length Constraints: Minimum length of 1\.

 ** [PaginationToken](#API_medical_DetectPHI_ResponseSyntax) **   <a name="comprehend-medical_DetectPHI-response-PaginationToken"></a>
 If the result of the previous request to `DetectPHI` was truncated, include the `PaginationToken` to fetch the next page of PHI entities\.   
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_medical_DetectPHI_Errors"></a>

For information about the errors that are common to all actions, see [Common Errors](CommonErrors.md)\.

 **InternalServerException**   
 An internal server error occurred\. Retry your request\.   
HTTP Status Code: 500

 **InvalidEncodingException**   
 The input text was not in valid UTF\-8 character encoding\. Check your text then retry your request\.  
HTTP Status Code: 400

 **InvalidRequestException**   
 The request that you made is invalid\. Check your request to determine why it's invalid and then retry the request\.  
HTTP Status Code: 400

 **ServiceUnavailableException**   
 The Amazon Comprehend Medical service is temporarily unavailable\. Please wait and then retry your request\.   
HTTP Status Code: 400

 **TextSizeLimitExceededException**   
 The size of the text you submitted exceeds the size limit\. Reduce the size of the text or use a smaller document and then retry your request\.   
HTTP Status Code: 400

 **TooManyRequestsException**   
 You have made too many requests within a short period of time\. Wait for a short time and then try your request again\. Contact customer support for more information about a service limit increase\.   
HTTP Status Code: 400

## See Also<a name="API_medical_DetectPHI_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/DetectPHI) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/DetectPHI) 