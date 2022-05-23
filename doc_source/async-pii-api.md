# Locating PII entities with asynchronous jobs \(API\)<a name="async-pii-api"></a>

Run an asynchronous batch job to locate PII in a collection of documents\. To run the job, upload your documents to Amazon S3, and submit a [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md) request\.

**Topics**
+ [Before you start](#detect-pii-before)
+ [Input parameters](#async-pii-api-inputs)
+ [Async Job methods](#async-pii-api-lifecycle)
+ [Output file format](#async-pii-api-outputs)
+ [Async analysis using the AWS Command Line Interface](#async-pii-api-cli)

## Before you start<a name="detect-pii-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input files and output files\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Input parameters<a name="async-pii-api-inputs"></a>

 In your request, include the following required parameters:
+ `InputDataConfig` – Provide an [InputDataConfig](API_InputDataConfig.md) definition for your request, which includes the input properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location of your input documents\.
+ `OutputDataConfig` – Provide an [OutputDataConfig](API_OutputDataConfig.md) definition for your request, which includes the output properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location where Amazon Comprehend writes the results of its analysis\.
+ `DataAccessRoleArn` – Provide the Amazon Resource Name \(ARN\) of an AWS Identity and Access Management role\. This role must grant Amazon Comprehend read access to your input data and write access to your output location in Amazon S3\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.
+ `Mode` – Set this parameter to `ONLY_OFFSETS`\. With this setting, the output provides the character offsets that locate each PII entity in the input text\. The output also includes confidence scores and PII entity types\.
+ `LanguageCode` – Set this parameter to `en`\. Amazon Comprehend supports PII detection in only English text\.

## Async Job methods<a name="async-pii-api-lifecycle"></a>

The `StartPiiEntitiesDetectionJob` returns a job ID, so that you can monitor the progress of the job and retrieve the job status when it completes\.

To monitor the progress of an analysis job, provide the job ID to the [DescribePiiEntitiesDetectionJob](API_DescribePiiEntitiesDetectionJob.md) operation\. The response from `DescribePiiEntitiesDetectionJob` contains the `JobStatus` field with the current status of the job\. A successful job transitions through the following states: 

SUBMITTED \-> IN\_PROGRESS \-> COMPLETED\. 

After an analysis job has finished \(`JobStatus` is COMPLETED, FAILED, or STOPPED\), use `DescribePiiEntitiesDetectionJob` to get the location of the results\. If the job status is `COMPLETED`, the response includes an `OutputDataConfig` field that contains a field with the Amazon S3 location of the output file\.

For additional details about the steps to follow for Amazon Comprehend async analysis, see [Asynchronous batch processing](concepts-processing-modes.md#how-async)\.

## Output file format<a name="async-pii-api-outputs"></a>

 The output file, `output.tar.gz`, is a compressed archive that contains the results of the analysis\.

The following is an example an output file from an analysis job that detected PII entities in documents\. The format of the input is one document per line\. 

```
{
  "Entities": [
    {
      "Type": "NAME",
      "BeginOffset": 40,
      "EndOffset": 69,
      "Score": 0.999995
    },
    {
      "Type": "ADDRESS",
      "BeginOffset": 247,
      "EndOffset": 253,
      "Score": 0.998828
    },
    {
      "Type": "BANK_ACCOUNT_NUMBER",
      "BeginOffset": 406,
      "EndOffset": 411,
      "Score": 0.693283
    }
  ],
  "File": "doc.txt",
  "Line": 0
},
{
  "Entities": [
    {
      "Type": "SSN",
      "BeginOffset": 1114,
      "EndOffset": 1124,
      "Score": 0.999999
    },
    {
      "Type": "EMAIL",
      "BeginOffset": 3742,
      "EndOffset": 3775,
      "Score": 0.999993
    },
    {
      "Type": "PIN",
      "BeginOffset": 4098,
      "EndOffset": 4102,
      "Score": 0.999995
    }
  ],
  "File": "doc.txt",
  "Line": 1
 }
```

The following is an example of output from an analysis where the format of the input is one document per file\.

```
{
  "Entities": [
    {
      "Type": "NAME",
      "BeginOffset": 40,
      "EndOffset": 69,
      "Score": 0.999995
    },
    {
      "Type": "ADDRESS",
      "BeginOffset": 247,
      "EndOffset": 253,
      "Score": 0.998828
    },
    {
      "Type": "BANK_ROUTING",
      "BeginOffset": 279,
      "EndOffset": 289,
      "Score": 0.999999
    }
  ],
  "File": "doc.txt"
}
```

## Async analysis using the AWS Command Line Interface<a name="async-pii-api-cli"></a>

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
  "Mode": "ONLY_OFFSETS"     
}
```

If the request to start the events detection job was successful, you will receive a response similar to the following:

```
{
  "JobId": "5d2fbe6e...e2c"
  "JobArn":  "arn:aws:comprehend:us-west-2:123456789012:pii-entities-detection-job/5d2fbe6e...e2c" 
  "JobStatus": "SUBMITTED",   
}
```

You can use the [DescribeEventsDetectionJob](API_DescribeEventsDetectionJob.md) operation to get the status of an existing job\. If the request to start the events detection job was successful, you will receive a response similar to the following:

```
aws comprehend describe-pii-entities-detection-job \
    --region region \
    --job-id job ID
```

When the job completes successfully, you receive a response similar to the following:

```
{
    "PiiEntitiesDetectionJobProperties": {
  "JobId": "5d2fbe6e...e2c"
  "JobArn":  "arn:aws:comprehend:us-west-2:123456789012:pii-entities-detection-job/5d2fbe6e...e2c" 
  "JobName": "piiCLItest3",
  "JobStatus": "COMPLETED",
  "SubmitTime": "2022-05-05T14:54:06.169000-07:00",
  "EndTime": "2022-05-05T15:00:17.007000-07:00",
  "InputDataConfig": {
       (identical to the input data that you provided with the request)
    }
}
```