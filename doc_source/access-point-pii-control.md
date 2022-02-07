# Controlling Access to Documents with Personally Identifiable Information \(PII\)<a name="access-point-pii-control"></a>

You can use an Amazon S3 Object Lambda Access Point to control access to documents with personally identifiable information \(PII\)\.

To ensure that only authorized users have access to documents that contain PII stored in your Amazon S3 bucket, you use the `ComprehendPiiAccessControlS3ObjectLambda` function\. This Lambda function uses the [ContainsPiiEntities](API_ContainsPiiEntities.md) operation when processing a standard Amazon S3 GET request on document objects\.

For example, if you have documents in your S3 bucket that include PII such as credit card numbers or bank account information, you can configure the `ComprehendPiiAccessControlS3ObjectLambda` function to detect these PII entity types and restrict access to unauthorized users\. For more information about supported PII entity types, see [PII Entity Types](how-pii.md#how-pii-types)\.

For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiAccessControlS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiAccessControlS3ObjectLambda) function in the AWS Serverless Application Repository\.

## Creating an Amazon S3 Object Lambda Access Point to Control Access to Documents<a name="s3-pii-control-object-lamdba"></a>

The following example creates an Amazon S3 Object Lambda Access Point to control access to documents that contain social security numbers\. 

### Creating an Amazon S3 Object Lambda Access Point Using the AWS Command Line Interface<a name="s3-pii-control-object-lamdba-cli"></a>

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

## Invoking an Amazon S3 Object Lambda Access Point to Control Access to Documents<a name="s3-pii-control-get-object"></a>

The following example invokes an Amazon S3 Object Lambda Access Point to control access to documents\.

### Invoking an Amazon S3 Object Lambda Access Point Using the AWS Command Line Interface<a name="s3-pii-control-get-object-cli"></a>

The following example invokes an Amazon S3 Object Lambda Access Point using the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws s3api get-object \
    --region region \
    --bucket s3-object-lambda-access-point-name-arn \
    --key object-prefix-key output-file-name
```