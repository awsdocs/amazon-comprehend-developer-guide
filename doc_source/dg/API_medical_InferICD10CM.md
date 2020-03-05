# InferICD10CM<a name="API_medical_InferICD10CM"></a>

InferICD10CM detects medical conditions as entities listed in a patient record and links those entities to normalized concept identifiers in the ICD\-10\-CM knowledge base from the Centers for Disease Control\. Amazon Comprehend Medical only detects medical entities in English language texts\.

## Request Syntax<a name="API_medical_InferICD10CM_RequestSyntax"></a>

```
{
   "[Text](#comprehend-medical_InferICD10CM-request-Text)": "string"
}
```

## Request Parameters<a name="API_medical_InferICD10CM_RequestParameters"></a>

For information about the parameters that are common to all actions, see [Common Parameters](CommonParameters.md)\.

The request accepts the following data in JSON format\.

 ** [Text](#API_medical_InferICD10CM_RequestSyntax) **   <a name="comprehend-medical_InferICD10CM-request-Text"></a>
The input text used for analysis\. The input for InferICD10CM is a string from 1 to 10000 characters\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 10000\.  
Required: Yes

## Response Syntax<a name="API_medical_InferICD10CM_ResponseSyntax"></a>

```
{
   "[Entities](#comprehend-medical_InferICD10CM-response-Entities)": [ 
      { 
         "[Attributes](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Attributes)": [ 
            { 
               "[BeginOffset](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-BeginOffset)": number,
               "[EndOffset](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-EndOffset)": number,
               "[Id](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-Id)": number,
               "[RelationshipScore](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-RelationshipScore)": number,
               "[Score](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-Score)": number,
               "[Text](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-Text)": "string",
               "[Traits](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-Traits)": [ 
                  { 
                     "[Name](API_medical_ICD10CMTrait.md#comprehend-Type-medical_ICD10CMTrait-Name)": "string",
                     "[Score](API_medical_ICD10CMTrait.md#comprehend-Type-medical_ICD10CMTrait-Score)": number
                  }
               ],
               "[Type](API_medical_ICD10CMAttribute.md#comprehend-Type-medical_ICD10CMAttribute-Type)": "string"
            }
         ],
         "[BeginOffset](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-BeginOffset)": number,
         "[Category](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Category)": "string",
         "[EndOffset](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-EndOffset)": number,
         "[ICD10CMConcepts](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-ICD10CMConcepts)": [ 
            { 
               "[Code](API_medical_ICD10CMConcept.md#comprehend-Type-medical_ICD10CMConcept-Code)": "string",
               "[Description](API_medical_ICD10CMConcept.md#comprehend-Type-medical_ICD10CMConcept-Description)": "string",
               "[Score](API_medical_ICD10CMConcept.md#comprehend-Type-medical_ICD10CMConcept-Score)": number
            }
         ],
         "[Id](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Id)": number,
         "[Score](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Score)": number,
         "[Text](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Text)": "string",
         "[Traits](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Traits)": [ 
            { 
               "[Name](API_medical_ICD10CMTrait.md#comprehend-Type-medical_ICD10CMTrait-Name)": "string",
               "[Score](API_medical_ICD10CMTrait.md#comprehend-Type-medical_ICD10CMTrait-Score)": number
            }
         ],
         "[Type](API_medical_ICD10CMEntity.md#comprehend-Type-medical_ICD10CMEntity-Type)": "string"
      }
   ],
   "[ModelVersion](#comprehend-medical_InferICD10CM-response-ModelVersion)": "string",
   "[PaginationToken](#comprehend-medical_InferICD10CM-response-PaginationToken)": "string"
}
```

## Response Elements<a name="API_medical_InferICD10CM_ResponseElements"></a>

If the action is successful, the service sends back an HTTP 200 response\.

The following data is returned in JSON format by the service\.

 ** [Entities](#API_medical_InferICD10CM_ResponseSyntax) **   <a name="comprehend-medical_InferICD10CM-response-Entities"></a>
The medical conditions detected in the text linked to ICD\-10\-CM concepts\. If the action is successful, the service sends back an HTTP 200 response, as well as the entities detected\.  
Type: Array of [ICD10CMEntity](API_medical_ICD10CMEntity.md) objects

 ** [ModelVersion](#API_medical_InferICD10CM_ResponseSyntax) **   <a name="comprehend-medical_InferICD10CM-response-ModelVersion"></a>
The version of the model used to analyze the documents, in the format *n*\.*n*\.*n* You can use this information to track the model used for a particular batch of documents\.  
Type: String  
Length Constraints: Minimum length of 1\.

 ** [PaginationToken](#API_medical_InferICD10CM_ResponseSyntax) **   <a name="comprehend-medical_InferICD10CM-response-PaginationToken"></a>
If the result of the previous request to `InferICD10CM` was truncated, include the `PaginationToken` to fetch the next page of medical condition entities\.   
Type: String  
Length Constraints: Minimum length of 1\.

## Errors<a name="API_medical_InferICD10CM_Errors"></a>

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

## See Also<a name="API_medical_InferICD10CM_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS Command Line Interface](https://docs.aws.amazon.com/goto/aws-cli/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for \.NET](https://docs.aws.amazon.com/goto/DotNetSDKV3/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for JavaScript](https://docs.aws.amazon.com/goto/AWSJavaScriptSDK/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for PHP V3](https://docs.aws.amazon.com/goto/SdkForPHPV3/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for Python](https://docs.aws.amazon.com/goto/boto3/comprehendmedical-2018-10-30/InferICD10CM) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/InferICD10CM) 