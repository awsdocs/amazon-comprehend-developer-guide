# Starting a custom entity detection job \(API\)<a name="detecting-cer-async-api"></a>

You can use the API to start and monitor an async analysis job for custom entity recognition\.

To start a custom entity detection job with the [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEntitiesDetectionJob.html) operation, you provide the EntityRecognizerArn, which is the Amazon Resource Name \(ARN\) of the trained model\. You can find this ARN in the response to the [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEntityRecognizer.html) operation\. 

**Topics**
+ [Detecting custom entities using the AWS Command Line Interface](#detecting-cer-async-api-cli)
+ [Detecting custom entities using the AWS SDK for Java](#detecting-cer-async-api-java)
+ [Detecting custom entities using the SDK for Python SDK for Python \(Boto3\)](#detecting-cer-async-api-python)
+ [Overriding API actions for PDF files](#detecting-cer-api-pdf)

## Detecting custom entities using the AWS Command Line Interface<a name="detecting-cer-async-api-cli"></a>

Use the following example for Unix, Linux, and macOS environments\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. To detect custom entities in a document set, use the following request syntax:

```
aws comprehend start-entities-detection-job \
     --entity-recognizer-arn "arn:aws:comprehend:region:account number:entity-recognizer/test-6" \
     --job-name infer-1 \
     --data-access-role-arn "arn:aws:iam::account number:role/service-role/AmazonComprehendServiceRole-role" \
     --language-code en \
     --input-data-config "S3Uri=s3://Bucket Name/Bucket Path" \
     --output-data-config "S3Uri=s3://Bucket Name/Bucket Path/" \
     --region region
```

Amazon Comprehend responds with the `JobID` and `JobStatus` and will return the output from the job in the S3 bucket that you specified in the request\.

## Detecting custom entities using the AWS SDK for Java<a name="detecting-cer-async-api-java"></a>

This example creates a custom entity recognizer, trains the model, and then runs it in an entity recognizer job using the AWS SDK for Java\.

```
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.DefaultAWSCredentialsProviderChain;
import com.amazonaws.services.comprehend.AmazonComprehend;
import com.amazonaws.services.comprehend.AmazonComprehendClientBuilder;
import com.amazonaws.services.comprehend.model.CreateEntityRecognizerRequest;
import com.amazonaws.services.comprehend.model.CreateEntityRecognizerResult;
import com.amazonaws.services.comprehend.model.DescribeEntityRecognizerRequest;
import com.amazonaws.services.comprehend.model.DescribeEntityRecognizerResult;
import com.amazonaws.services.comprehend.model.EntityRecognizerAnnotations;
import com.amazonaws.services.comprehend.model.EntityRecognizerDocuments;
import com.amazonaws.services.comprehend.model.EntityRecognizerInputDataConfig;
import com.amazonaws.services.comprehend.model.EntityTypesListItem;
import com.amazonaws.services.comprehend.model.InputDataConfig;
import com.amazonaws.services.comprehend.model.LanguageCode;
import com.amazonaws.services.comprehend.model.OutputDataConfig;
import com.amazonaws.services.comprehend.model.StartEntitiesDetectionJobRequest;
import com.amazonaws.services.comprehend.model.StartEntitiesDetectionJobResult;

public class CustomEntityRecognizerDemo {

    public static void main(String[] args) {
        // Create credentials using a provider chain. For more information, see
        // https://docs.aws.amazon.com/sdk-for-java/v1/developer-guide/credentials.html
        AWSCredentialsProvider awsCreds = DefaultAWSCredentialsProviderChain.getInstance();

        AmazonComprehend comprehendClient =
                AmazonComprehendClientBuilder.standard()
                        .withCredentials(awsCreds)
                        .withRegion("region")
                        .build();

        final String dataAccessRoleArn = "arn:aws:iam::account number:role/service-role/AmazonComprehendServiceRole-role";

        final CreateEntityRecognizerRequest createEntityRecognizerRequest = new CreateEntityRecognizerRequest()
                .withRecognizerName("recognizer name")
                .withDataAccessRoleArn(dataAccessRoleArn)
                .withLanguageCode(LanguageCode.En)
                .withInputDataConfig(new EntityRecognizerInputDataConfig()
                    .withEntityTypes(new EntityTypesListItem().withType("PERSON"))
                    .withDocuments(new EntityRecognizerDocuments()
                            .withS3Uri("s3://Bucket Name/Bucket Path/documents"))
                    .withAnnotations(new EntityRecognizerAnnotations()
                            .withS3Uri("s3://Bucket Name/Bucket Path/annotations")));

        final CreateEntityRecognizerResult createEntityRecognizerResult = comprehendClient.createEntityRecognizer(createEntityRecognizerRequest);
        final String entityRecognizerArn = createEntityRecognizerResult.getEntityRecognizerArn();
        System.out.println("Entity Recognizer ARN: " + entityRecognizerArn);

        DescribeEntityRecognizerRequest describeEntityRecognizerRequest = new DescribeEntityRecognizerRequest()
                .withEntityRecognizerArn(entityRecognizerArn);
        final DescribeEntityRecognizerResult describeEntityRecognizerResult = comprehendClient.describeEntityRecognizer(describeEntityRecognizerRequest);
        System.out.println("describeEntityRecognizerResult: " + describeEntityRecognizerResult);

        if ("TRAINED".equals(describeEntityRecognizerResult.getEntityRecognizerProperties().getStatus())) {
            // After model gets trained, launch an job to extract entities.
            final StartEntitiesDetectionJobRequest startEntitiesDetectionJobRequest = new StartEntitiesDetectionJobRequest()
                    .withJobName("Inference Job Name")
                    .withEntityRecognizerArn(entityRecognizerArn)
                    .withDataAccessRoleArn(dataAccessRoleArn)
                    .withLanguageCode(LanguageCode.En)
                    .withInputDataConfig(new InputDataConfig()
                            .withS3Uri("s3://Bucket Name/Bucket Path"))
                    .withOutputDataConfig(new OutputDataConfig()
                            .withS3Uri("s3://Bucket Name/Bucket Path/"));

            final StartEntitiesDetectionJobResult startEntitiesDetectionJobResult = comprehendClient.startEntitiesDetectionJob(startEntitiesDetectionJobRequest);
            System.out.println("startEntitiesDetectionJobResult: " + startEntitiesDetectionJobResult);
        }
    }

}
```

## Detecting custom entities using the SDK for Python SDK for Python \(Boto3\)<a name="detecting-cer-async-api-python"></a>

This example creates a custom entity recognizer, trains the model, and then runs it in an entity recognizer job using the AWS SDK for Python \(Boto3\)\.

Instantiate the SDK for Python\. 

```
import boto3
import uuid
comprehend = boto3.client("comprehend", region_name="region")
```

Create an entity recognizer: 

```
response = comprehend.create_entity_recognizer(
    RecognizerName="Recognizer-Name-Goes-Here-{}".format(str(uuid.uuid4())),
    LanguageCode="en",
    DataAccessRoleArn="Role ARN",
    InputDataConfig={
        "EntityTypes": [
            {
                "Type": "ENTITY_TYPE"
            }
        ],
        "Documents": {
            "S3Uri": "s3://Bucket Name/Bucket Path/documents"
        },
        "Annotations": {
            "S3Uri": "s3://Bucket Name/Bucket Path/annotations"
        }
    }
)
recognizer_arn = response["EntityRecognizerArn"]
```

List all recognizers: 

```
response = comprehend.list_entity_recognizers()
```

Wait for the entity recognizer to reach TRAINED status: 

```
while True:
    response = comprehend.describe_entity_recognizer(
        EntityRecognizerArn=recognizer_arn
    )

    status = response["EntityRecognizerProperties"]["Status"]
    if "IN_ERROR" == status:
        sys.exit(1)
    if "TRAINED" == status:
        break

    time.sleep(10)
```

Start a custom entities detection job: 

```
response = comprehend.start_entities_detection_job(
    EntityRecognizerArn=recognizer_arn,
    JobName="Detection-Job-Name-{}".format(str(uuid.uuid4())),
    LanguageCode="en",
    DataAccessRoleArn="Role ARN",
    InputDataConfig={
        "InputFormat": "ONE_DOC_PER_LINE",
        "S3Uri": "s3://Bucket Name/Bucket Path/documents"
    },
    OutputDataConfig={
        "S3Uri": "s3://Bucket Name/Bucket Path/output"
    }
)
```

## Overriding API actions for PDF files<a name="detecting-cer-api-pdf"></a>

For image files and PDF files, you can override the default extraction actions using the `DocumentReaderConfig` parameter in `InputDataConfig`\.

The following example defines a JSON file named myInputDataConfig\.json to set the `InputDataConfig` values\. It sets `DocumentReadConfig` to use the Amazon Textract `DetectDocumentText` API for all PDF files\.

**Example**  

```
"InputDataConfig": {
  "S3Uri": s3://Bucket Name/Bucket Path",
  "InputFormat": "ONE_DOC_PER_FILE",
  "DocumentReaderConfig": {
      "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT",
      "DocumentReadMode": "FORCE_DOCUMENT_READ_ACTION"
  }
}
```

In the `StartEntitiesDetectionJob` operation, specify the myInputDataConfig\.json file as the `InputDataConfig` parameter:

```
  --input-data-config file://myInputDataConfig.json  
```

For more information about the `DocumentReaderConfig` parameters, see [Setting text extraction options](idp-set-textract-options.md)\.