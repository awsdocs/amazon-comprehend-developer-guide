# ComprehendMedicalAsyncJobProperties<a name="API_medical_ComprehendMedicalAsyncJobProperties"></a>

Provides information about a detection job\.

## Contents<a name="API_medical_ComprehendMedicalAsyncJobProperties_Contents"></a>

 **DataAccessRoleArn**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-DataAccessRoleArn"></a>
The Amazon Resource Name \(ARN\) that gives Amazon Comprehend Medical read access to your input data\.  
Type: String  
Length Constraints: Minimum length of 20\. Maximum length of 2048\.  
Pattern: `arn:aws(-[^:]+)?:iam::[0-9]{12}:role/.+`   
Required: No

 **EndTime**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-EndTime"></a>
The time that the detection job completed\.  
Type: Timestamp  
Required: No

 **ExpirationTime**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ExpirationTime"></a>
The date and time that job metadata is deleted from the server\. Output files in your S3 bucket will not be deleted\. After the metadata is deleted, the job will no longer appear in the results of the `ListEntitiesDetectionV2Job` or the `ListPHIDetectionJobs` operation\.  
Type: Timestamp  
Required: No

 **InputDataConfig**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-InputDataConfig"></a>
The input data configuration that you supplied when you created the detection job\.  
Type: [InputDataConfig](API_medical_InputDataConfig.md) object  
Required: No

 **JobId**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobId"></a>
The identifier assigned to the detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 32\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobName**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobName"></a>
The name that you assigned to the detection job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 256\.  
Pattern: `^([\p{L}\p{Z}\p{N}_.:/=+\-%@]*)$`   
Required: No

 **JobStatus**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-JobStatus"></a>
The current status of the detection job\. If the status is `FAILED`, the `Message` field shows the reason for the failure\.  
Type: String  
Valid Values:` SUBMITTED | IN_PROGRESS | COMPLETED | PARTIAL_SUCCESS | FAILED | STOP_REQUESTED | STOPPED`   
Required: No

 **KMSKey**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-KMSKey"></a>
The AWS Key Management Service key, if any, used to encrypt the output files\.   
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 2048\.  
Pattern: `.*`   
Required: No

 **LanguageCode**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-LanguageCode"></a>
The language code of the input documents\.  
Type: String  
Valid Values:` en`   
Required: No

 **ManifestFilePath**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ManifestFilePath"></a>
The path to the file that describes the results of a batch job\.  
Type: String  
Length Constraints: Minimum length of 1\. Maximum length of 4096\.  
Required: No

 **Message**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-Message"></a>
A description of the status of a job\.  
Type: String  
Required: No

 **ModelVersion**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-ModelVersion"></a>
The version of the model used to analyze the documents\. The version number looks like X\.X\.X\. You can use this information to track the model used for a particular batch of documents\.  
Type: String  
Required: No

 **OutputDataConfig**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-OutputDataConfig"></a>
The output data configuration that you supplied when you created the detection job\.  
Type: [OutputDataConfig](API_medical_OutputDataConfig.md) object  
Required: No

 **SubmitTime**   <a name="comprehend-Type-medical_ComprehendMedicalAsyncJobProperties-SubmitTime"></a>
The time that the detection job was submitted for processing\.  
Type: Timestamp  
Required: No

## See Also<a name="API_medical_ComprehendMedicalAsyncJobProperties_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehendmedical-2018-10-30/ComprehendMedicalAsyncJobProperties) 
+  [AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehendmedical-2018-10-30/ComprehendMedicalAsyncJobProperties) 
+  [AWS SDK for Java](https://docs.aws.amazon.com/goto/SdkForJava/comprehendmedical-2018-10-30/ComprehendMedicalAsyncJobProperties) 
+  [AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehendmedical-2018-10-30/ComprehendMedicalAsyncJobProperties) 