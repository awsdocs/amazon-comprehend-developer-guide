# Train custom entity recognizers \(API\)<a name="train-cer-model"></a>

To create and train a custom entity recognition model, use the Amazon Comprehend [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEntityRecognizer.html) API operation

**Topics**
+ [Training custom entity recognizers using the AWS Command Line Interface](#get-started-api-cer-cli)
+ [Training custom entity recognizers using the AWS SDK for Java](#get-started-api-cer-java)
+ [Training custom entity recognizers using Python \(Boto3\)](#cer-python)

## Training custom entity recognizers using the AWS Command Line Interface<a name="get-started-api-cer-cli"></a>

The following examples demonstrate using the `CreateEntityRecognizer` operation and other associated APIs with the AWS CLI\. 

The examples are formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

Create a custom entity recognizer using the `create-entity-recognizer` CLI command\. For information about the input\-data\-config parameter, see [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_CreateEntityRecognizer.html) in the *Amazon Comprehend API Reference*\.

```
aws comprehend create-entity-recognizer \
     --language-code en \
     --recognizer-name test-6 \
     --data-access-role-arn "arn:aws:iam::account number:role/service-role/AmazonComprehendServiceRole-role" \
     --input-data-config "EntityTypes=[{Type=PERSON}],Documents={S3Uri=s3://Bucket Name/Bucket Path/documents},
                Annotations={S3Uri=s3://Bucket Name/Bucket Path/annotations}" \
     --region region
```

List all entity recognizers in a Region using the `list-entity-recognizers` CLI command\.\.

```
aws comprehend list-entity-recognizers \
     --region region
```

Check Job Status of custom entity recognizers using the `describe-entity-recognizer` CLI command\.\.

```
aws comprehend describe-entity-recognizer \
     --entity-recognizer-arn arn:aws:comprehend:region:account number:entity-recognizer/test-6 \
     --region region
```

## Training custom entity recognizers using the AWS SDK for Java<a name="get-started-api-cer-java"></a>

This example creates a custom entity recognizer and trains the model, using Java

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

    }

}
```

## Training custom entity recognizers using Python \(Boto3\)<a name="cer-python"></a>

Instantiate Boto3 SDK: 

```
import boto3
import uuid
comprehend = boto3.client("comprehend", region_name="region")
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