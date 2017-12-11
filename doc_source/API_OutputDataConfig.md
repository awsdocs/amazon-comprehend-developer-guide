# OutputDataConfig<a name="API_OutputDataConfig"></a>

Provides configuration parameters for the output of topic detection jobs\.



## Contents<a name="API_OutputDataConfig_Contents"></a>

 **S3Uri**   
When you use the `OutputDataConfig` object with the `StartTopicsDetectionJob` operation, you specify the Amazon S3 location where you want to write the output data\. The URI must be in the same region as the API endpoint that you are calling\. The location is used as the prefix for the actual location of the output file\.  
When the topic detection job is finished, the service creates an output file in a directory specific to the job\. The `S3Uri` field contains the location of the output file, called `output.tar.gz`\. It is a compressed archive that contains two files, `topic-terms.csv` that lists the terms associated with each topic, and `doc-topics.csv` that lists the documents associated with each topic\. For more information, see [Topic Modeling](topic-modeling.md)\.  
Type: String  
Length Constraints: Maximum length of 1024\.  
Pattern: `s3://([^/]+)(/.*)?`   
Required: Yes

## See Also<a name="API_OutputDataConfig_SeeAlso"></a>

For more information about using this API in one of the language\-specific AWS SDKs, see the following:

+  [AWS SDK for C\+\+](http://docs.aws.amazon.com/goto/SdkForCpp/comprehend-2017-11-27/OutputDataConfig) 

+  [AWS SDK for Go](http://docs.aws.amazon.com/goto/SdkForGoV1/comprehend-2017-11-27/OutputDataConfig) 

+  [AWS SDK for Java](http://docs.aws.amazon.com/goto/SdkForJava/comprehend-2017-11-27/OutputDataConfig) 

+  [AWS SDK for Ruby V2](http://docs.aws.amazon.com/goto/SdkForRubyV2/comprehend-2017-11-27/OutputDataConfig) 