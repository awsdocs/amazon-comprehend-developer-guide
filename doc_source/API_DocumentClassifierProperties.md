# DocumentClassifierProperties<a name="API_DocumentClassifierProperties"></a>

Provides information about a document classifier\.

## Contents<a name="API_DocumentClassifierProperties_Contents"></a>

 **ClassifierMetadata**   <a name="comprehend-Type-DocumentClassifierProperties-ClassifierMetadata"></a>
Information about the document classifier, including the number of documents used for training the classifier, the number of documents used for test the classifier, and an accuracy rating\.  
Type: [ClassifierMetadata](API_ClassifierMetadata.md) object  
Required: No

 **DataAccessRoleArn**   <a name="comprehend-Type-DocumentClassifierProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) of the AWS Identity and Management \(IAM\) role that grants Amazon Comprehend read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **DocumentClassifierArn**   <a name="comprehend-Type-DocumentClassifierProperties-DocumentClassifierArn"></a>
The Amazon Resource Name \(ARN\) that identifies the document classifier\.  
Type: String  
Length Constraints: Maximum length of 256\.  
Pattern: `arn:aws:comprehend:[a-zA-Z0-9-]*:[0-9]{12}:document-classifier/[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: No

 **EndTime**   <a name="comprehend-Type-DocumentClassifierProperties-EndTime"></a>
The time that training the document classifier completed\.  
Type: Timestamp  
Required: No

 **InputDataConfig**   <a name="comprehend-Type-DocumentClassifierProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the document classifier for training\.  
Type: [DocumentClassifierInputDataConfig](API_DocumentClassifierInputDataConfig.md) object  
Required: No

 **LanguageCode**   <a name="comprehend-Type-DocumentClassifierProperties-LanguageCode"></a>
The language code for the language of the documents that the classifier was trained on\.  
Type: String  
Valid Values:` en | es | fr | de | it | pt`   
Required: No

 **Message**   <a name="comprehend-Type-DocumentClassifierProperties-Message"></a>
Additional information about the status of the classifier\.  
Type: String  
Required: No

 **Status**   <a name="comprehend-Type-DocumentClassifierProperties-Status"></a>
The status of the document classifier\. If the status is `TRAINED` the classifier is ready to use\. If the status is `FAILED` you can see additional information about why the classifier wasn't trained in the `Message` field\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 **SubmitTime**   <a name="comprehend-Type-DocumentClassifierProperties-SubmitTime"></a>
The time that the document classifier was submitted for training\.  
Type: Timestamp  
Required: No

 **TrainingEndTime**   <a name="comprehend-Type-DocumentClassifierProperties-TrainingEndTime"></a>
The time that training of the document classifier was completed\. Indicates the time when the training completes on documentation classifiers\. You are billed for the time interval between this time and the value of TrainingStartTime\.  
Type: Timestamp  
Required: No

 **TrainingStartTime**   <a name="comprehend-Type-DocumentClassifierProperties-TrainingStartTime"></a>
Indicates the time when the training starts on documentation classifiers\. You are billed for the time interval between this time and the value of TrainingEndTime\.   
Type: Timestamp  
Required: No

## See Also<a name="API_DocumentClassifierProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentClassifierProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentClassifierProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/DocumentClassifierProperties) 
+  [AWS SDK for Ruby V2](https://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/DocumentClassifierProperties) 