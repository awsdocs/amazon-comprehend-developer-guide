# Real\-time analysis for custom classification \(API\)<a name="class-sync-api"></a>

You can use the Amazon Comprehend API to run real\-time classification with a custom model\. First, you create an endpoint to run the real\-time analysis\. After you create the endpoint, you run the real\-time classification\.

The examples in this section use command formats for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

For information about provisioning endpoint throughput, and the associated costs, see [Using Amazon Comprehend endpoints](using-endpoints.md)\.

**Topics**
+ [Creating an endpoint for custom classification](#create-endpoint-api)
+ [Running real\-time custom classification](#cc-real-time-analysis-api)

## Creating an endpoint for custom classification<a name="create-endpoint-api"></a>

The following example shows the [CreateEndpoint](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEndpoint.html) API operation using the AWS CLI\. 

```
aws comprehend create-endpoint \
    --desired-inference-units number of inference units \
    --endpoint-name endpoint name \
    --model-arn arn:aws:comprehend:region:account-id:model/example \
    --tags Key=My1stTag,Value=Value1
```

Amazon Comprehend responds with the following:

```
{
   "EndpointArn": "Arn"
}
```

## Running real\-time custom classification<a name="cc-real-time-analysis-api"></a>

After you create an endpoint for your custom classification model, you use the endpoint to run the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) API operation\. You can provide text input using the `text` or `bytes` parameter\. Enter the other input types using the `bytes` parameter\.

For image files and PDF files, you can use the `DocumentReaderConfig` parameter to override the default text extraction actions\. For details, see [Setting text extraction options](idp-set-textract-options.md)

**Topics**
+ [Running real\-time custom classification using the AWS Command Line Interface](#cc-real-time-analysis-api-cli)
+ [Running custom classification analysis using the AWS SDK for Java](#api-customclass-java)
+ [Running custom classification analysis using the AWS SDK for Python \(Boto\)](#api-customclass-python)

### Running real\-time custom classification using the AWS Command Line Interface<a name="cc-real-time-analysis-api-cli"></a>

The following example demonstrates using the *classify\-document* CLI command\. 

#### Detecting entities in semi\-structured documents using the AWS CLI<a name="cc-real-time-analysis-api-run-cli1"></a>

**Example Use the CLI to run real\-time analysis using input text**  

```
aws comprehend classify-document \
     --endpoint-arn arn:aws:comprehend:region:account-id:endpoint/endpoint name \
     --text 'From the Tuesday, April 16th, 1912 edition of The Guardian newspaper: The maiden voyage of the White Star liner Titanic, 
     the largest ship ever launched ended in disaster. The Titanic started her trip from Southampton for New York on Wednesday. Late 
     on Sunday night she struck an iceberg off the Grand Banks of Newfoundland. By wireless telegraphy she sent out signals of distress, 
     and several liners were near enough to catch and respond to the call.'
```
Amazon Comprehend responds with the following:  

```
{
    "Classes": [ 
       { 
          "Name": "string",
          "Score": 0.9793661236763
       }
    ]
 }
```

#### Use the CLI to run real\-time classification for a semi\-structured document<a name="cc-real-time-analysis-api-run-cli2"></a>

To analyze custom classification for a PDF, Word, or image file, run the `classify-document` command with the input file in the `bytes` parameter\.

**Example Use the CLI to classification on an image file**  
This example shows how to pass the image file using the `fileb` option to base\-64 encode the image bytes\. For more information, see [Binary large objects](https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-parameters-types.html#parameter-type-blob) in the AWS Command Line Interface User Guide\.   
This example also passes in a JSON file named `config.json` to set the text extraction options\.  

```
$ aws comprehend classify-document \
> --endpoint-arn arn \
> --language-code en \
> --bytes fileb://image1.jpg   \
> --document-reader-config file://config.json
```
The config\.json file contains the following content\.  

```
 {
    "DocumentReadMode": "FORCE_DOCUMENT_READ_ACTION",
    "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT"    
 }
```
Amazon Comprehend responds with the following:  

```
{
    "Classes": [ 
       { 
          "Name": "string",
          "Score": 0.9793661236763
       }
    ]
 }
```

For more information, see [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) in the Amazon Comprehend API Reference\.

### Running custom classification analysis using the AWS SDK for Java<a name="api-customclass-java"></a>

This example creates a custom classifier and trains it using Java\.

```
import com.amazonaws.services.comprehend.AmazonComprehend;
 
  
 import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
 import com.amazonaws.services.comprehend.model.DescribeDocumentClassificationJobRequest;
 import com.amazonaws.services.comprehend.model.DescribeDocumentClassificationJobResult;
 import com.amazonaws.services.comprehend.model.InputDataConfig;
 import com.amazonaws.services.comprehend.model.InputFormat;
 import com.amazonaws.services.comprehend.model.ListDocumentClassificationJobsRequest;
 import com.amazonaws.services.comprehend.model.ListDocumentClassificationJobsResult;
 import com.amazonaws.services.comprehend.model.OutputDataConfig;
 import com.amazonaws.services.comprehend.model.StartDocumentClassificationJobRequest;
 import com.amazonaws.services.comprehend.model.StartDocumentClassificationJobResult;
 
 public class DocumentClassificationDemo {
 
     public static void main(String[] args) {
 
         final AmazonComprehend comprehendClient =
             AmazonComprehendClientBuilder.standard()
                                          .withRegion("region")
                                          .build();
 
         final String dataAccessRoleArn = "arn:aws:iam::account number:role/resource name";
 
         final StartDocumentClassificationJobRequest startDocumentClassificationJobRequest = new StartDocumentClassificationJobRequest()
             .withDocumentClassifierArn("arn:aws:comprehend:region:account number:document-classifier/SampleCodeClassifier1")
             .withDataAccessRoleArn(dataAccessRoleArn)
             .withInputDataConfig(new InputDataConfig()
                 .withS3Uri("s3://srikad-us-west-2-input/docclass/smalltrain").withInputFormat(InputFormat.ONE_DOC_PER_LINE))
             .withOutputDataConfig(new OutputDataConfig().withS3Uri("s3://resource name/output"));
 
         final StartDocumentClassificationJobResult startDocumentClassificationJobResult =
             comprehendClient.startDocumentClassificationJob(startDocumentClassificationJobRequest);
         final String jobId = startDocumentClassificationJobResult.getJobId();
 
         System.out.println("Document classification jobId: " + jobId);
 
         final DescribeDocumentClassificationJobRequest describeDocumentClassificationJobRequest =
             new DescribeDocumentClassificationJobRequest().withJobId(jobId);
         final DescribeDocumentClassificationJobResult describeDocumentClassificationJobResult =
             comprehendClient.describeDocumentClassificationJob(describeDocumentClassificationJobRequest);
         System.out.println("DescribeDocumentClassificationJobResult: " + describeDocumentClassificationJobResult);
 
         final ListDocumentClassificationJobsRequest listDocumentClassificationJobsRequest =
             new ListDocumentClassificationJobsRequest();
 
         final ListDocumentClassificationJobsResult listDocumentClassificationJobsResult = comprehendClient
             .listDocumentClassificationJobs(listDocumentClassificationJobsRequest);
         System.out.println("ListDocumentClassificationJobsResult: " + listDocumentClassificationJobsResult);
     }
 
 }
```

### Running custom classification analysis using the AWS SDK for Python \(Boto\)<a name="api-customclass-python"></a>

 

This example runs a custom classifier job using Python\.

```
import boto3
 
 
 # Instantiate Boto3 SDK:
 client = boto3.client('comprehend', region_name='region')
 
 start_response = client.start_document_classification_job(
     InputDataConfig={
         'S3Uri': 's3://srikad-us-west-2-input/docclass/file name',
         'InputFormat': 'ONE_DOC_PER_LINE'
     },
     OutputDataConfig={
         'S3Uri': 's3://S3Bucket/output'
     },
     DataAccessRoleArn='arn:aws:iam::account number:role/resource name',
     DocumentClassifierArn=
     'arn:aws:comprehend:region:account number:document-classifier/SampleCodeClassifier1'
 )
 
 print("Start response: %s\n", start_response)
 
 # Check the status of the job
 describe_response = client.describe_document_classification_job(JobId=start_response['JobId'])
 print("Describe response: %s\n", describe_response)
 
 # List all classification jobs in account
 list_response = client.list_document_classification_jobs()
 print("List response: %s\n", list_response)
```