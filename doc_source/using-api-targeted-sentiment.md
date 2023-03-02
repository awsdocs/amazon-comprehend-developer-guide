# Async analysis for targeted sentiment<a name="using-api-targeted-sentiment"></a>

For information about real\-time analysis for Targeted sentiment, see [Real\-time analysis for targeted sentiment](using-api-sync.md#get-started-api-targeted-sentiment)\.

Amazon Comprehend provides the following API operations to start and manage asynchronous targeted sentiment analysis:
+  [StartTargetedSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartTargetedSentimentDetectionJob.html) – Starts an asynchronous targeted sentiment detection job for a collection of documents\.
+  [ListTargetedSentimentDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ListTargetedSentimentDetectionJobs.html) – Returns the list of targeted sentiment detection jobs that you have submitted\.
+  [DescribeTargetedSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeTargetedSentimentDetectionJob.html) – Gets the properties \(including status\) associated with the specified targeted sentiment detection job\.
+  [StopTargetedSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StopTargetedSentimentDetectionJob.html) – Stops the specified in\-progress targeted sentiment job\.

**Topics**
+ [Before you start](#api-targeted-sentiment-before)
+ [Analyzing targeted sentiment using the AWS CLI](#api-targeted-sentiment-cli)

## Before you start<a name="api-targeted-sentiment-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input and output\. The buckets must be in the same Region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-based permissions required for asynchronous operations](security_iam_id-based-policy-examples.md#auth-role-permissions)\.

## Analyzing targeted sentiment using the AWS CLI<a name="api-targeted-sentiment-cli"></a>

The following example demonstrates using the `StartTargetedSentimentDetectionJob` operation with the AWS CLI\. This example specifies the language of the input text\.

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend start-targeted-sentiment-detection-job \
       --job-name "job name" \
       --language-code "en" \
       --cli-input-json file://path to JSON input file
```

For the `cli-input-json` parameter you supply the path to a JSON file that contains the request data, as shown in the following example\.

```
{
    "InputDataConfig": {
        "S3Uri": "s3://input bucket/input path",
        "InputFormat": "ONE_DOC_PER_FILE"
    },
    "OutputDataConfig": {
        "S3Uri": "s3://output bucket/output path"
    },
    "DataAccessRoleArn": "arn:aws:iam::account ID:role/data access role"
}
```

If the request to start the job was successful, you will receive the following response:

```
{
    "JobStatus": "SUBMITTED",
    "JobArn": "job ARN"
    "JobId": "job ID"
}
```