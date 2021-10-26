# Detecting Custom Entities<a name="get-started-cer"></a>

To create the custom entities in a document, use the Amazon Comprehend [ CreateEntityRecognizer ](API_CreateEntityRecognizer.md) to create an entity recognizer\. To identify those custom entities, use the [ StartEntitiesDetectionJob ](API_StartEntitiesDetectionJob.md) operation\. 

**Topics**
+ [Creating and Detecting Custom Entities Using the AWS Command Line Interface](#get-started-api-cer-cli)
+ [Detecting Custom Entities Using the AWS SDK for Java](#get-started-api-cer-java)
+ [Detecting Custom Entities Using the AWS SDK for Python \(Boto3\)](#cer-python)

## Creating and Detecting Custom Entities Using the AWS Command Line Interface<a name="get-started-api-cer-cli"></a>

The following examples demonstrates using the `CreateEntityRecognizer` operation, `StartEntitiesDetectionJob` operation and other associated APIs with the AWS CLI\. 

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Creating a custom entity recognizer using the `CreateEntityRecognizer` operation\.

```
aws comprehend create-entity-recognizer \
     --language-code en \
     --recognizer-name test-6 \
     --data-access-role-arn "arn:aws:iam::account number:role/service-role/AmazonComprehendServiceRole-role" \
     --input-data-config "EntityTypes=[{Type=PERSON}],Documents={S3Uri=s3://Bucket Name/Bucket Path/documents},
                Annotations={S3Uri=s3://Bucket Name/Bucket Path/annotations}" \
     --region region
```

Listing all entity recognizers in a region using the `ListEntityRecognizers` operation\.

```
aws comprehend list-entity-recognizers \
     --region region
```

Checking Job Status of custom entity recognizers using the `DescribeEntityRecognizer` operation\.

```
aws comprehend describe-entity-recognizer \
     --entity-recognizer-arn arn:aws:comprehend:region:account number:entity-recognizer/test-6 \
     --region region
```

Starting a custom entities recognition job using the `StartEntitiesDetectionJob` operation\.

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

## Detecting Custom Entities Using the AWS SDK for Java<a name="get-started-api-cer-java"></a>

This example creates a custom entity recognizer, trains the model, and then runs it in an entity recognizer job using Java

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

## Detecting Custom Entities Using the AWS SDK for Python \(Boto3\)<a name="cer-python"></a>

Instantiate Boto3 SDK: 

```
import boto3
import uuid
comprehend = boto3.client("comprehend", region_name="recognizer name")
```

Create entity recognizer: 

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

Wait for recognizer to reach TRAINED status: 

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

Start entities detection job: 

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