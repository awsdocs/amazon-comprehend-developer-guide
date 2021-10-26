# EntityRecognizerInputDataConfig<a name="API_EntityRecognizerInputDataConfig"></a>

Specifies the format and location of the input data\.

## Contents<a name="API_EntityRecognizerInputDataConfig_Contents"></a>

 ** Annotations **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-Annotations"></a>
The S3 location of the CSV file that annotates your training documents\.  
Type: [ EntityRecognizerAnnotations ](API_EntityRecognizerAnnotations.md) object  
Required: No

 ** AugmentedManifests **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-AugmentedManifests"></a>
A list of augmented manifest files that provide training data for your custom model\. An augmented manifest file is a labeled dataset that is produced by Amazon SageMaker Ground Truth\.  
This parameter is required if you set `DataFormat` to `AUGMENTED_MANIFEST`\.  
Type: Array of [ AugmentedManifestsListItem ](API_AugmentedManifestsListItem.md) objects  
Required: No

 ** DataFormat **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-DataFormat"></a>
The format of your training data:  
+  `COMPREHEND_CSV`: A CSV file that supplements your training documents\. The CSV file contains information about the custom entities that your trained model will detect\. The required format of the file depends on whether you are providing annotations or an entity list\.

  If you use this value, you must provide your CSV file by using either the `Annotations` or `EntityList` parameters\. You must provide your training documents by using the `Documents` parameter\.
+  `AUGMENTED_MANIFEST`: A labeled dataset that is produced by Amazon SageMaker Ground Truth\. This file is in JSON lines format\. Each line is a complete JSON object that contains a training document and its labels\. Each label annotates a named entity in the training document\. 

  If you use this value, you must provide the `AugmentedManifests` parameter in your request\.
If you don't specify a value, Amazon Comprehend uses `COMPREHEND_CSV` as the default\.  
Type: String  
Valid Values:` COMPREHEND_CSV | AUGMENTED_MANIFEST`   
Required: No

 ** Documents **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-Documents"></a>
The S3 location of the folder that contains the training documents for your custom entity recognizer\.  
This parameter is required if you set `DataFormat` to `COMPREHEND_CSV`\.  
Type: [ EntityRecognizerDocuments ](API_EntityRecognizerDocuments.md) object  
Required: No

 ** EntityList **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-EntityList"></a>
The S3 location of the CSV file that has the entity list for your custom entity recognizer\.  
Type: [ EntityRecognizerEntityList ](API_EntityRecognizerEntityList.md) object  
Required: No

 ** EntityTypes **   <a name="comprehend-Type-EntityRecognizerInputDataConfig-EntityTypes"></a>
The entity types in the labeled training data that Amazon Comprehend uses to train the custom entity recognizer\. Any entity types that you don't specify are ignored\.  
A maximum of 25 entity types can be used at one time to train an entity recognizer\. Entity types must not contain the following invalid characters: \\n \(line break\), \\\\n \(escaped line break\), \\r \(carriage return\), \\\\r \(escaped carriage return\), \\t \(tab\), \\\\t \(escaped tab\), space, and , \(comma\)\.   
Type: Array of [ EntityTypesListItem ](API_EntityTypesListItem.md) objects  
Required: Yes

## See Also<a name="API_EntityRecognizerInputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerInputDataConfig) 