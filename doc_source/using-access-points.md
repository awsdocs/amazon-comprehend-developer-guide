# Using Amazon S3 object Lambda access points for personally identifiable information \(PII\)<a name="using-access-points"></a>

Use Amazon S3 Object Lambda Access Points for personally identifiable information \(PII\) to configure how documents are retrieved from your Amazon S3 bucket\. You can control access to documents that contain PII and redact PII from documents\. For more information on how Amazon Comprehend can detect PII in your documents, see [PII entities](how-pii.md)\. Amazon S3 Object Lambda Access Points use AWS Lambda functions to automatically transform the output of a standard Amazon S3 GET request\. For more information see, [Transforming objects with S3 object Lambda](https://docs.aws.amazon.com/AmazonS3/latest/userguide/transforming-objects.html) in the *Amazon Simple Storage Service User Guide*\. 

When you create an Amazon S3 Object Lambda Access Point for PII, documents are processed using Amazon Comprehend Lambda functions to control access of documents that contain PII and redact PII from documents\.

When you create an Amazon S3 Object Lambda Access Point for PII, documents are processed using the following Amazon Comprehend Lambda functions:


+ `ComprehendPiiAccessControlS3ObjectLambda` \- Controls access to documents with PII stored in your S3 bucket\. For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiAccessControlS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiAccessControlS3ObjectLambda) function in the AWS Serverless Application Repository\. 
+ `ComprehendPiiRedactionS3ObjectLambda` \- Redacts PII from documents in your Amazon S3 bucket\. For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiRedactionS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiRedactionS3ObjectLambda) function in the AWS Serverless Application Repository\.

For information about how to deploy serverless applications from the AWS Serverless Application Repository, see [Deploying applications](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/serverlessrepo-consuming-applications.html) in the *AWS Serverless Application Repository Developer Guide*\.

**Topics**
+ [Controlling access to documents with personally identifiable information \(PII\)](#access-point-pii-control)
+ [Redacting personally identifiable information \(PII\) from documents](#access-point-pii-redact)

## Controlling access to documents with personally identifiable information \(PII\)<a name="access-point-pii-control"></a>

You can use an Amazon S3 Object Lambda Access Point to control access to documents with personally identifiable information \(PII\)\.

To ensure that only authorized users have access to documents that contain PII stored in your Amazon S3 bucket, you use the `ComprehendPiiAccessControlS3ObjectLambda` function\. This Lambda function uses the [ContainsPiiEntities](API_ContainsPiiEntities.md) operation when processing a standard Amazon S3 GET request on document objects\.

For example, if you have documents in your S3 bucket that include PII such as credit card numbers or bank account information, you can configure the `ComprehendPiiAccessControlS3ObjectLambda` function to detect these PII entity types and restrict access to unauthorized users\. For more information about supported PII entity types, see [PII entity types](how-pii.md#how-pii-types)\.

For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiAccessControlS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiAccessControlS3ObjectLambda) function in the AWS Serverless Application Repository\.

### Creating an Amazon S3 object Lambda access point to control access to documents<a name="s3-pii-control-object-lamdba"></a>

The following example creates an Amazon S3 Object Lambda Access Point to control access to documents that contain social security numbers\. 

#### Creating an Amazon S3 object Lambda access point using the AWS Command Line Interface<a name="s3-pii-control-object-lamdba-cli"></a>

Create an Amazon S3 Object Lambda Access Point configuration and save the configuration in a file called **config\.json**\.

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
                    "FunctionArn": "comprehend-pii-access-control-s3-object-lambda-arn",
                    "FunctionPayload": "{\"pii_entities_types\": \"SSN\"}"
                }
            }
        }
    ]
}
```

The following example creates an Amazon S3 Object Lambda Access Point based on the configuration defined in the `config.json` file\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3control create-banner-access-point \     
    --region region \
    --account-id account-id \
    --name s3-object-lambda-access-point \
    --configuration file://config.json
```

### Invoking an Amazon S3 object Lambda access point to control access to documents<a name="s3-pii-control-get-object"></a>

The following example invokes an Amazon S3 Object Lambda Access Point to control access to documents\.

#### Invoking an Amazon S3 object Lambda access point using the AWS Command Line Interface<a name="s3-pii-control-get-object-cli"></a>

The following example invokes an Amazon S3 Object Lambda Access Point using the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3api get-object \
    --region region \
    --bucket s3-object-lambda-access-point-name-arn \
    --key object-prefix-key output-file-name
```

## Redacting personally identifiable information \(PII\) from documents<a name="access-point-pii-redact"></a>

You can use an Amazon S3 Object Lambda Access Point to redact personally identifiable information \(PII\) from documents\. 

To redact PII entity types from documents stored in an S3 bucket, you use the `ComprehendPiiRedactionS3ObjectLambda` function\. This Lambda function uses the [ContainsPiiEntities](API_ContainsPiiEntities.md) and [DetectPiiEntities](API_DetectPiiEntities.md) operations when processing a standard Amazon S3 GET request on document objects\.

For example, if documents in your S3 bucket include PII such as credit card numbers or bank account information, you can configure the `ComprehendPiiRedactionS3ObjectLambda` function to detect PII and then return a copy of these documents in which PII entity types are redacted\. For more information about supported PII entity types, see [PII entity types](how-pii.md#how-pii-types)\.

For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiRedactionS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiRedactionS3ObjectLambda) function in the AWS Serverless Application Repository\.

### Creating an Amazon S3 object Lambda access point to redact PII from documents<a name="s3-pii-control-object-lamdba"></a>

The following example creates an Amazon S3 Object Lambda Access Point to redeact credit card numbers from documents\.

#### Creating an Amazon S3 object Lambda access point using the AWS Command Line Interface<a name="s3-pii-control-object-lamdba-cli"></a>

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

### Invoking an Amazon S3 object Lambda access point to redact PII from documents<a name="s3-pii-control-get-object"></a>

The following examples invoke an Amazon S3 Object Lambda Access Point to redact PII from documents\.

#### Invoking an Amazon S3 object Lambda access point using the AWS Command Line Interface<a name="s3-pii-control-get-object-cli"></a>

The following example invokes an Amazon S3 Object Lambda Access Point using the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3api get-object \
    --region region \
    --bucket s3-object-lambda-access-point-name-arn \
    --key object-prefix-key output-file-name
```