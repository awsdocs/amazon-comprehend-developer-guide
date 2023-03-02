# Train custom classifiers \(API\)<a name="train-custom-classifier-api"></a>

To create and train a custom classifier, use the [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateDocumentClassifier.html) operation\.

You can monitor the progress of the request using the [DescribeDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeDocumentClassifier.html) operation\. Once the `Status` field is `TRAINED` you can then use the classifier to classify documents\.

**Topics**
+ [Training custom classification using the AWS Command Line Interface](#get-started-api-customclass-cli)
+ [Training custom classifiers using the AWS SDK for Java](#get-started-api-customclass-java)
+ [Training custom classificiers using the AWS SDK for Python \(Boto\)](#get-started-api-customclass-python)

## Training custom classification using the AWS Command Line Interface<a name="get-started-api-customclass-cli"></a>

The following examples demonstrate using the `CreateDocumentClassifier` operation, the `DescribeDocumentClassificationJob` operation, and other custom classifier APIs with the AWS CLI\. 

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Create a custom classifier using the `create-document-classifier` operation\.

```
aws comprehend create-document-classifier \
     --region region \
     --document-classifier-name testDelete \
     --language-code en \
     --input-data-config S3Uri=s3://S3Bucket/docclass/file name \
     --data-access-role-arn arn:aws:iam::account number:role/testFlywheelDataAccess
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

## Training custom classifiers using the AWS SDK for Java<a name="get-started-api-customclass-java"></a>

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

## Training custom classificiers using the AWS SDK for Python \(Boto\)<a name="get-started-api-customclass-python"></a>

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