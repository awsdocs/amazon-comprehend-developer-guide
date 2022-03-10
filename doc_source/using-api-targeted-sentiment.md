# Analyzing Targeted Sentiment<a name="using-api-targeted-sentiment"></a>

Amazon Comprehend provides the following API operations for analyzing targeted sentiment:
+ [StartTargetedSentimentDetectionJob](API_StartTargetedSentimentDetectionJob.md) – Starts an asynchronous targeted sentiment detection job for a collection of documents\.
+ [ListTargetedSentimentDetectionJobs](API_ListTargetedSentimentDetectionJobs.md) – Returns the list of targeted sentiment detection jobs that you have submitted\.
+ [DescribeTargetedSentimentDetectionJob](API_DescribeTargetedSentimentDetectionJob.md) – Gets the properties \(including status\) associated with the specified targeted sentiment detection job\.
+ [StopTargetedSentimentDetectionJob](API_StopTargetedSentimentDetectionJob.md) – Stops the specified in\-progress targeted sentiment job\.

**Topics**
+ [Before You Start](#api-targeted-sentiment-before)
+ [Analyzing Targeted Sentiment Using the AWS CLI](#api-targeted-sentiment-cli)

## Before You Start<a name="api-targeted-sentiment-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input and output\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Analyzing Targeted Sentiment Using the AWS CLI<a name="api-targeted-sentiment-cli"></a>

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