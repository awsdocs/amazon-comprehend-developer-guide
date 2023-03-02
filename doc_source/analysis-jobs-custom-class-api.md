# Analysis jobs for custom classification \(API\)<a name="analysis-jobs-custom-class-api"></a>

After you [create and train](train-custom-classifier-api.md) a custom document classifier, you can use the classifier to run analysis jobs\.

Use the [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html) operation to start classifying unlabeled documents\. You specify the S3 bucket that contains the input documents, the S3 bucket for the output documents, and the classifier to use\.

 [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartDocumentClassificationJob.html) is asynchronous\. Once you have started the job, use the [DescribeDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeDocumentClassificationJob.html) operation to monitor its progress\. When the `Status` field in the response shows `COMPLETED`, you can access the output in the location that you specified\.

**Topics**
+ [Run a classification job using the AWS Command Line Interface](#get-started-api-customclass-cli)
+ [Run a classification job using the AWS SDK for Java](#get-started-api-customclass-java)
+ [Run a classification job using the AWS SDK for Python \(Boto\)](#get-started-api-customclass-python)

## Run a classification job using the AWS Command Line Interface<a name="get-started-api-customclass-cli"></a>

The following examples the `StartDocumentClassificationJob` operation, and other custom classifier APIs with the AWS CLI\. 

The following examples use the command format for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Run a custom classification job using the `StartDocumentClassificationJob` operation\.

```
aws comprehend start-document-classification-job \
     --region region \
     --document-classifier-arn arn:aws:comprehend:region:account number:document-classifier/testDelete \
     --input-data-config S3Uri=s3://S3Bucket/docclass/file name,InputFormat=ONE_DOC_PER_LINE \
     --output-data-config S3Uri=s3://S3Bucket/output \
     --data-access-role-arn arn:aws:iam::account number:role/resource name
```

Get information on a custom classifier with the job id using the `DescribeDocumentClassificationJob` operation\.

```
aws comprehend describe-document-classification-job \
     --region region \
     --job-id job id
```

List all custom classification jobs in your account using the `ListDocumentClassificationJobs` operation\.

```
aws comprehend list-document-classification-jobs
     --region region
```

## Run a classification job using the AWS SDK for Java<a name="get-started-api-customclass-java"></a>

This example runs a custom classifier job using Java\.

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

## Run a classification job using the AWS SDK for Python \(Boto\)<a name="get-started-api-customclass-python"></a>

 

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