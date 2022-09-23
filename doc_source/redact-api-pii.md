# Redacting PII entities with asynchronous jobs \(API\)<a name="redact-api-pii"></a>

To redact the PII entities in your text, you start an asynchronous batch job\. To run the job, upload your documents to Amazon S3, and submit a [StartPiiEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartPiiEntitiesDetectionJob.html) request\. 

**Topics**
+ [Before you start](#redact-pii-before)
+ [Input parameters](#redact-pii-api-inputs)
+ [Output file format](#redact-pii-api-outputs)
+ [PII redaction using the AWS Command Line Interface](#redact-pii-api-cli)

## Before you start<a name="redact-pii-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input files and output files\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Input parameters<a name="redact-pii-api-inputs"></a>

In your request, include the following required parameters:
+ `InputDataConfig` – Provide an [InputDataConfig](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_InputDataConfig.html) definition for your request, which includes the input properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location of your input documents\.
+ `OutputDataConfig` – Provide an [OutputDataConfig](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_OutputDataConfig.html) definition for your request, which includes the output properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location where Amazon Comprehend writes the results of its analysis\.
+ `DataAccessRoleArn` – Provide the Amazon Resource Name \(ARN\) of an AWS Identity and Access Management role\. This role must grant Amazon Comprehend read access to your input data and write access to your output location in Amazon S3\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.
+ `Mode` – Set this parameter to `ONLY_REDACTION`\. With this setting, Amazon Comprehend writes a copy of your input documents to the output location in Amazon S3\. In this copy, each PII entity is redacted\.
+ `RedactionConfig` – Provide an [RedactionConfig](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_RedactionConfig.html) definition for your request, which includes the configuration parameters for the redaction\. Specify the types of PII to redact, and specify whether each PII entity is replaced with the name of its type or a character of your choice:
  + Specify the PII entity types to redact in the `PiiEntityTypes` array\. To redact all entity types, set the array value to `["ALL"]`\.
  + To replace each PII entity with its type, set the `MaskMode` parameter to `REPLACE_WITH_PII_ENTITY_TYPE`\. For example, with this setting, the PII entity "Jane Doe" is replaced with "\[NAME\]"\.
  + To replace the characters in each PII entity with a character of your choice, set the `MaskMode` parameter to `MASK`, and set the `MaskCharacter` parameter to the replacement character\. Provide only a single character\. Valid characters are \!, \#, $, %, &, \*, and @\. For example, with this setting, the PII entity "Jane Doe" can be replaced with "\*\*\*\* \*\*\*"
+ `LanguageCode` – Set this parameter to `en`\. Amazon Comprehend supports PII detection in only English text\.

## Output file format<a name="redact-pii-api-outputs"></a>

The following example shows the input and output files from an analysis job that redacts PII\. The format of the input is one document per line\. 

```
{
Managing Your Accounts Primary Branch Canton John Doe Phone Number 443-573-4800 123 Main StreetBaltimore, MD 21224
Online Banking HowardBank.com  Telephone 1-877-527-2703 Bank 3301 Boston Street, Baltimore, MD 21224
```

The analysis job to redact this input file produces the following output file\.

```
{
Managing Your Accounts Primary Branch ****** ******** Phone Number ************ **********************************
Online Banking **************  Telephone ************** Bank ***************************************     
 }
```

## PII redaction using the AWS Command Line Interface<a name="redact-pii-api-cli"></a>

The following example uses the `StartPiiEntitiesDetectionJob` operation with the AWS CLI\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend start-pii-entities-detection-job \
    --region region \
    --job-name job name \
    --cli-input-json file://path to JSON input file
```

For the `cli-input-json` parameter you supply the path to a JSON file that contains the request data, as shown in the following example\.

```
{
    "InputDataConfig": {
        "S3Uri": "s3://input bucket/input path",
        "InputFormat": "ONE_DOC_PER_LINE"
    },
    "OutputDataConfig": {
        "S3Uri": "s3://output bucket/output path"
    },
    "DataAccessRoleArn": "arn:aws:iam::account ID:role/data access role"
    "LanguageCode": "en",
    "Mode": "ONLY_REDACTION"
    "RedactionConfig": {
        "MaskCharacter": "*",
        "MaskMode": "MASK",
        "PiiEntityTypes": ["ALL"]
    }
}
```

If the request to start the events detection job was successful, you will receive a response similar to the following:

```
{
  "JobId": "7c4fbe6e...e5b"
  "JobArn":  "arn:aws:comprehend:us-west-2:123456789012:pii-entities-detection-job/7c4fbe6e...e5b" 
  "JobStatus": "SUBMITTED",   
}
```

You can use the [DescribeEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeEventsDetectionJob.html) operation to get the status of an existing job\. 

```
aws comprehend describe-pii-entities-detection-job \
    --region region \
    --job-id job ID
```

When the job completes successfully, you receive a response similar to the following:

```
{
  "PiiEntitiesDetectionJobProperties": {
     "JobId": "7c4fbe6e...e5b"
     "JobArn":  "arn:aws:comprehend:us-west-2:123456789012:pii-entities-detection-job/7c4fbe6e...e5b" 
     "JobName": "piiCLIredtest1",
     "JobStatus": "COMPLETED",
     "SubmitTime": "2022-05-05T14:54:06.169000-07:00",
     "EndTime": "2022-05-05T15:00:17.007000-07:00",
     "InputDataConfig": {
        (identical to the input data that you provided with the request)
  }
}
```