# EntityRecognizerInputDataConfig<a name="API_EntityRecognizerInputDataConfig"></a>

Specifies the format and location of the input data\.

## Contents<a name="API_EntityRecognizerInputDataConfig_Contents"></a>

 **Annotations**   <a name="comprehend-Type-EntityRecognizerInputDataConfig-Annotations"></a>
S3 location of the annotations file for an entity recognizer\.  
Type: [EntityRecognizerAnnotations](API_EntityRecognizerAnnotations.md) object  
Required: No

 **Documents**   <a name="comprehend-Type-EntityRecognizerInputDataConfig-Documents"></a>
S3 location of the documents folder for an entity recognizer  
Type: [EntityRecognizerDocuments](API_EntityRecognizerDocuments.md) object  
Required: Yes

 **EntityList**   <a name="comprehend-Type-EntityRecognizerInputDataConfig-EntityList"></a>
S3 location of the entity list for an entity recognizer\.  
Type: [EntityRecognizerEntityList](API_EntityRecognizerEntityList.md) object  
Required: No

 **EntityTypes**   <a name="comprehend-Type-EntityRecognizerInputDataConfig-EntityTypes"></a>
The entity types in the input data for an entity recognizer\. A maximum of 12 entity types can be used at one time to train an entity recognizer\.  
Type: Array of [EntityTypesListItem](API_EntityTypesListItem.md) objects  
Required: Yes

## See Also<a name="API_EntityRecognizerInputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 