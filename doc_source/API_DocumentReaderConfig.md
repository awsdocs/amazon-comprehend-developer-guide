# DocumentReaderConfig<a name="API_DocumentReaderConfig"></a>

The input properties for a topic detection job\.

## Contents<a name="API_DocumentReaderConfig_Contents"></a>

 ** DocumentReadAction **   <a name="comprehend-Type-DocumentReaderConfig-DocumentReadAction"></a>
This enum field will start with two values which will apply to PDFs:  
+  `TEXTRACT_DETECT_DOCUMENT_TEXT` \- The service calls DetectDocumentText for PDF documents per page\.
+  `TEXTRACT_ANALYZE_DOCUMENT` \- The service calls AnalyzeDocument for PDF documents per page\.
Type: String  
Valid Values:` TEXTRACT_DETECT_DOCUMENT_TEXT | TEXTRACT_ANALYZE_DOCUMENT`   
Required: Yes

 ** DocumentReadMode **   <a name="comprehend-Type-DocumentReaderConfig-DocumentReadMode"></a>
This enum field provides two values:  
+  `SERVICE_DEFAULT` \- use service defaults for Document reading\. For Digital PDF it would mean using an internal parser instead of Textract APIs
+  `FORCE_DOCUMENT_READ_ACTION` \- Always use specified action for DocumentReadAction, including Digital PDF\. 
Type: String  
Valid Values:` SERVICE_DEFAULT | FORCE_DOCUMENT_READ_ACTION`   
Required: No

 ** FeatureTypes **   <a name="comprehend-Type-DocumentReaderConfig-FeatureTypes"></a>
Specifies how the text in an input file should be processed:  
Type: Array of strings  
Array Members: Minimum number of 1 item\. Maximum number of 2 items\.  
Valid Values:` TABLES | FORMS`   
Required: No

## See Also<a name="API_DocumentReaderConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:
+  [ AWS SDK for C\+\+](https://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/DocumentReaderConfig) 
+  [ AWS SDK for Go](https://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/DocumentReaderConfig) 
+  [ AWS SDK for Java V2](https://docs.aws.amazon.com/goto/SdkForJavaV2/comprehend-2017-11-27/DocumentReaderConfig) 
+  [ AWS SDK for Ruby V3](https://docs.aws.amazon.com/goto/SdkForRubyV3/comprehend-2017-11-27/DocumentReaderConfig) 