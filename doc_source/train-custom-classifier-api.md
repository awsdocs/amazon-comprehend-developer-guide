# Train and run custom classifiers \(API\)<a name="train-custom-classifier-api"></a>

To create and train a custom classifier, use the [CreateDocumentClassifier](API_CreateDocumentClassifier.md) operation\. To identify custom classifiers in a corpus of documents, use the [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) operation\. 

**Topics**
+ [Using custom classification with the AWS Command Line Interface](#get-started-api-customclass-cli)
+ [Using custom classification using the AWS SDK for Java](#get-started-api-customclass-java)
+ [Using custom classification using the AWS SDK for Python \(Boto\)](#get-started-api-customclass-python)

## Using custom classification with the AWS Command Line Interface<a name="get-started-api-customclass-cli"></a>

The following examples demonstrate using the `CreateDocumentClassifier` operation, `StartDocumentClassificationJob` operation, and other custom classifier APIs with the AWS CLI\. 

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Create a custom classifier using the `create-document-classifier` operation\.

```
aws comprehend create-document-classifier \
     --region region \
     --document-classifier-name testDelete \
     --language-code en \
     --input-data-config S3Uri=s3://S3Bucket/docclass/file name \
     --data-access-role-arn arn:aws:iam::account number:role/testDeepInsightDataAccess
```

Get information on a custom classifier with the document classifier ARN using the `DescribeDocumentClassifier` operation\.

```
aws comprehend describe-document-classifier \
     --region region \
     --document-classifier-arn arn:aws:comprehend:region:account number:document-classifier/file name
```

Delete a custom classifier using the `DeleteDocumentClassifier` operation\.

```
aws comprehend delete-document-classifier \
     --region region \
     --document-classifier-arn arn:aws:comprehend:region:account number:document-classifier/testDelete
```

List all custom classifiers in the account using the `ListDocumentClassifiers` operation\.

```
aws comprehend list-document-classifiers
     --region region
```

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

Create an endpoint associated with a specific custom model using the `CreateEndpoint` operation\.

```
aws comprehend create-endpoint \
    --desired-inference-units number of inference units \
    --endpoint-name endpoint name \
    --model-arn arn:aws:comprehend:region:account-id:model/example \
    --tags Key=My1stTag,Value=Value1
```

Run a custom classification request using an endpoint by using the `ClassifyDocument` operation\. 

```
aws comprehend classify-document \
    --endpoint-arn arn:aws:comprehend:region:account-id:endpoint/endpoint name \
    --text 'text.'
```

Update an endpoint using the `UpdateEndpoint` operation\.

```
aws comprehend update-endpoint \
    --desired-inference-units updated number of inference units \
    --endpoint-arn arn:aws:comprehend:region:account-id:endpoint/endpoint name
```

Delete an endpoint using the `DeleteEndpoint` operation\.

```
aws comprehend delete-endpoint \
    --endpoint-arn arn:aws:comprehend:region:account-idendpoint/endpoint name
```

Get information on an endpoint with the endpoint Arn using the `DescribeEndpoint` operation\. 

```
aws comprehend describe-endpoint \
    --endpoint-arn arn:aws:comprehend:region:account-id:endpoint/endpoint name
```

List all endpoints in your account using the `ListEndpoints` operation\.

```
aws comprehend list-endpoint \
    --filter status=Ready
    --max-results 50
```

## Using custom classification using the AWS SDK for Java<a name="get-started-api-customclass-java"></a>

This example creates a custom classifier and trains it using Java

```
import com.amazonaws.services.comprehend.AmazonComprehend;

import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.CreateDocumentClassifierRequest;
import com.amazonaws.services.comprehend.model.CreateDocumentClassifierResult;
import com.amazonaws.services.comprehend.model.DescribeDocumentClassifierRequest;
import com.amazonaws.services.comprehend.model.DescribeDocumentClassifierResult;
import com.amazonaws.services.comprehend.model.DocumentClassifierInputDataConfig;
import com.amazonaws.services.comprehend.model.LanguageCode;
import com.amazonaws.services.comprehend.model.ListDocumentClassifiersRequest;
import com.amazonaws.services.comprehend.model.ListDocumentClassifiersResult;

public class DocumentClassifierDemo {

    public static void main(String[] args) {
        final AmazonComprehend comprehendClient =
            AmazonComprehendClientBuilder.standard()
                                         .withRegion("us-west-2")
                                         .build();

        final String dataAccessRoleArn = "arn:aws:iam::account number:role/resource name";

        final CreateDocumentClassifierRequest createDocumentClassifierRequest = new CreateDocumentClassifierRequest()
            .withDocumentClassifierName("SampleCodeClassifier")
            .withDataAccessRoleArn(dataAccessRoleArn)
            .withLanguageCode(LanguageCode.En)
            .withInputDataConfig(new DocumentClassifierInputDataConfig()
                .withS3Uri("s3://S3Bucket/docclass/file name"));

        final CreateDocumentClassifierResult createDocumentClassifierResult =
            comprehendClient.createDocumentClassifier(createDocumentClassifierRequest);
        final String documentClassifierArn = createDocumentClassifierResult.getDocumentClassifierArn();

        System.out.println("Document Classifier ARN: " + documentClassifierArn);

        final DescribeDocumentClassifierRequest describeDocumentClassifierRequest = new DescribeDocumentClassifierRequest()
            .withDocumentClassifierArn(documentClassifierArn);
        final DescribeDocumentClassifierResult describeDocumentClassifierResult = comprehendClient.describeDocumentClassifier(describeDocumentClassifierRequest);
        System.out.println("DescribeDocumentClassifierResult: " + describeDocumentClassifierResult);

        final ListDocumentClassifiersRequest listDocumentClassifiersRequest = new ListDocumentClassifiersRequest();

        final ListDocumentClassifiersResult listDocumentClassifiersResult = comprehendClient
            .listDocumentClassifiers(listDocumentClassifiersRequest);
        System.out.println("ListDocumentClassifierResult: " + listDocumentClassifiersResult );
    }
}
```

## Using custom classification using the AWS SDK for Python \(Boto\)<a name="get-started-api-customclass-python"></a>

This example creates a custom classifier and trains it using Python

```
import boto3


# Instantiate Boto3 SDK:
client = boto3.client('comprehend', region_name='region')

# Create a document classifier
create_response = client.create_document_classifier(
    InputDataConfig={
        'S3Uri': 's3://S3Bucket/docclass/file name'
    },
    DataAccessRoleArn='arn:aws:iam::account number:role/resource name',
    DocumentClassifierName='SampleCodeClassifier1',
    LanguageCode='en'
)
print("Create response: %s\n", create_response)

# Check the status of the classifier
describe_response = client.describe_document_classifier(
    DocumentClassifierArn=create_response['DocumentClassifierArn'])
print("Describe response: %s\n", describe_response)

# List all classifiers in account
list_response = client.list_document_classifiers()
print("List response: %s\n", list_response)
```

This example runs a custom classifier job using Python

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