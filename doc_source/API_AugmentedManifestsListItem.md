# AugmentedManifestsListItem<a name="API_AugmentedManifestsListItem"></a>

An augmented manifest file that provides training data for your custom model\. An augmented manifest file is a labeled dataset that is produced by Amazon SageMaker Ground Truth\.

## Contents<a name="API_AugmentedManifestsListItem_Contents"></a>

 ** AnnotationDataS3Uri **   <a name="comprehend-Type-AugmentedManifestsListItem-AnnotationDataS3Uri"></a>
The S3 prefix to the annotation files that are referred in the augmented manifest file\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: No

 ** AttributeNames **   <a name="comprehend-Type-AugmentedManifestsListItem-AttributeNames"></a>
The JSON attribute that contains the annotations for your training documents\. The number of attribute names that you specify depends on whether your augmented manifest file is the output of a single labeling job or a chained labeling job\.  
If your file is the output of a single labeling job, specify the LabelAttributeName key that was used when the job was created in Ground Truth\.  
If your file is the output of a chained labeling job, specify the LabelAttributeName key for one or more jobs in the chain\. Each LabelAttributeName key provides the annotations from an individual job\.  
Type: Array of strings  
Length Constraints: Minimum length of 1\. Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*`   
Required: Yes

 ** DocumentType **   <a name="comprehend-Type-AugmentedManifestsListItem-DocumentType"></a>
The type of augmented manifest\. PlainTextDocument or SemiStructuredDocument\. If you don't specify, the default is PlainTextDocument\.   
+  `PLAIN_TEXT_DOCUMENT` A document type that represents any unicode text that is encoded in UTF\-8\.
+  `SEMI_STRUCTURED_DOCUMENT` A document type with positional and structural context, like a PDF\. For training with Amazon Comprehend, only PDFs are supported\. For inference, Amazon Comprehend support PDFs, DOCX and TXT\.
Type: String  
Valid Values:` PLAIN_TEXT_DOCUMENT | SEMI_STRUCTURED_DOCUMENT`   
Required: No

 ** S3Uri **   <a name="comprehend-Type-AugmentedManifestsListItem-S3Uri"></a>
The Amazon S3 location of the augmented manifest file\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: Yes

 ** SourceDocumentsS3Uri **   <a name="comprehend-Type-AugmentedManifestsListItem-SourceDocumentsS3Uri"></a>
The S3 prefix to the source files \(PDFs\) that are referred to in the augmented manifest file\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://[a-z0-9][\.\-a-z0-9]{1,61}[a-z0-9](/.*)?`   
Required: No

 ** Split **   <a name="comprehend-Type-AugmentedManifestsListItem-Split"></a>
The purpose of the data you've provided in the augmented manifest\. You can either train or test this data\. If you don't specify, the default is train\.  
TRAIN \- all of the documents in the manifest will be used for training\. If no test documents are provided, Amazon Comprehend will automatically reserve a portion of the training documents for testing\.  
 TEST \- all of the documents in the manifest will be used for testing\.  
Type: String  
Valid Values:` TRAIN | TEST`   
Required: No

## See Also<a name="API_AugmentedManifestsListItem_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/AugmentedManifestsListItem) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/AugmentedManifestsListItem) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/AugmentedManifestsListItem) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/AugmentedManifestsListItem) 