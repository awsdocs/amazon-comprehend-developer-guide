# Redacting Personally Identifiable Information \(PII\) from Documents<a name="access-point-pii-redact"></a>

You can use an Amazon S3 Object Lambda Access Point to redact personally identifiable information \(PII\) from documents\. 

To redact PII entity types from documents stored in an S3 bucket, you use the `ComprehendPiiRedactionS3ObjectLambda` function\. This Lambda function uses the [ContainsPiiEntities](API_ContainsPiiEntities.md) and [DetectPiiEntities](API_DetectPiiEntities.md) operations when processing a standard Amazon S3 GET request on document objects\.

For example, if documents in your S3 bucket include PII such as credit card numbers or bank account information, you can configure the `ComprehendPiiRedactionS3ObjectLambda` function to detect PII and then return a copy of these documents in which PII entity types are redacted\. For more information about supported PII entity types, see [PII Entity Types](how-pii.md#how-pii-types)\.

For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiRedactionS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiRedactionS3ObjectLambda) function in the AWS Serverless Application Repository\.

## Creating an Amazon S3 Object Lambda Access Point to Redact PII from Documents<a name="s3-pii-control-object-lamdba"></a>

The following example creates an Amazon S3 Object Lambda Access Point to redeact credit card numbers from documents\.

### Creating an Amazon S3 Object Lambda Access Point Using the AWS Command Line Interface<a name="s3-pii-control-object-lamdba-cli"></a>

Create an Amazon S3 Object Lambda Access Point configuration and save the configuration in a file called `config.json`\.

```
{
    "SupportingAccessPoint": "s3-default-access-point-name-arn",
    "TransformationConfigurations": [
        {
            "Actions": [
                "s3:GetObject"
            ],
            "ContentTransformation": {
                "AwsLambda": {
                    "FunctionArn": "comprehend-pii-redaction-s3-object-lambda-arn",
                    "FunctionPayload": "{\"pii_entities_types\": \"CREDIT_DEBIT_NUMBER\"}"
                }
            }
        }
    ]
}
```

The following example demonstrates creating an Amazon S3 Object Lambda Access Point based on the configuration defined in the `config.json`

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3control create-access-point-for-object-lambda \     
    --region region \
    --account-id account-id \
    --name s3-object-lambda-access-point \
    --configuration file://config.json
```

## Invoking an Amazon S3 Object Lambda Access Point to Redact PII from Documents<a name="s3-pii-control-get-object"></a>

The following examples invoke an Amazon S3 Object Lambda Access Point to redact PII from documents\.

### Invoking an Amazon S3 Object Lambda Access Point Using the AWS Command Line Interface<a name="s3-pii-control-get-object-cli"></a>

The following example invokes an Amazon S3 Object Lambda Access Point using the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3api get-object \
    --region region \
    --bucket s3-object-lambda-access-point-name-arn \
    --key object-prefix-key output-file-name
```