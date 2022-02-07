# EntityRecognizerSummary<a name="API_EntityRecognizerSummary"></a>

 Describes the information about an entity recognizer and its versions\.

## Contents<a name="API_EntityRecognizerSummary_Contents"></a>

 ** LatestVersionCreatedAt **   <a name="comprehend-Type-EntityRecognizerSummary-LatestVersionCreatedAt"></a>
 The time that the latest entity recognizer version was submitted for processing\.  
Type: Timestamp  
Required: No

 ** LatestVersionName **   <a name="comprehend-Type-EntityRecognizerSummary-LatestVersionName"></a>
 The version name you assigned to the latest entity recognizer version\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

 ** LatestVersionStatus **   <a name="comprehend-Type-EntityRecognizerSummary-LatestVersionStatus"></a>
 Provides the status of the latest entity recognizer version\.  
Type: String  
Valid Values:` SUBMITTED | TRAINING | DELETING | STOP_REQUESTED | STOPPED | IN_ERROR | TRAINED`   
Required: No

 ** NumberOfVersions **   <a name="comprehend-Type-EntityRecognizerSummary-NumberOfVersions"></a>
 The number of versions you created\.  
Type: Integer  
Required: No

 ** RecognizerName **   <a name="comprehend-Type-EntityRecognizerSummary-RecognizerName"></a>
 The name that you assigned the entity recognizer\.  
Type: String  
Length Constraints: Maximum length of 63\.  
Pattern: `^[a-zA-Z0-9](-*[a-zA-Z0-9])*$`   
Required: No

## See Also<a name="API_EntityRecognizerSummary_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/EntityRecognizerSummary) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/EntityRecognizerSummary) 
+  [AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/EntityRecognizerSummary) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/EntityRecognizerSummary) 