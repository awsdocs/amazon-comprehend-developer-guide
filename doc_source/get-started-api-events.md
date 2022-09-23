# Async analysis for event detection<a name="get-started-api-events"></a>

**Topics**
+ [Before you start](#events-before)
+ [Detect events using the AWS CLI](#events-cli)
+ [List events using the AWS CLI](#list-events)
+ [Describe events using the AWS CLI](#describe-events)
+ [Get events detection results](#async-events)

To detect events in a document set, use the [StartEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEventsDetectionJob.html) to start an asynchronous job\.

## Before you start<a name="events-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input and output\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Detect events using the AWS CLI<a name="events-cli"></a>

The following example demonstrates using the [StartEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEventsDetectionJob.html) operation with the AWS CLI

The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend start-events-detection-job \
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
  "TargetEventTypes": [
      "BANKRUPTCY",
      "EMPLOYMENT",
      "CORPORATE_ACQUISITION",
      "INVESTMENT_GENERAL",
      "CORPORATE_MERGER",
      "IPO",
      "RIGHTS_ISSUE",
      "SECONDARY_OFFERING",
      "SHELF_OFFERING",
      "TENDER_OFFERING",
      "STOCK_SPLIT"
  ]
}
```

If the request to start the events detection job was successful, you will receive the following response:

```
{
  "JobStatus": "SUBMITTED",
  "JobId": "job ID"
}
```

## List events using the AWS CLI<a name="list-events"></a>

Use the [ListEventsDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ListEventsDetectionJobs.html) operation to see a list of the events detection jobs that you have submitted\. The list includes information about the input and output locations that you used and the status of each of the detection jobs\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend list-events-detection-jobs --region region 
```

You will get JSON similar to the following in response:

```
{
 "EventsDetectionJobPropertiesList": [
    {
       "DataAccessRoleArn": "arn:aws:iam::account ID:role/data access role",
       "EndTime": timestamp,
       "InputDataConfig": {
          "InputFormat": "ONE_DOC_PER_LINE",
          "S3Uri": "s3://input bucket/input path"
       },
       "JobId": "job ID",
       "JobName": "job name",
       "JobStatus": "COMPLETED",
       "LanguageCode": "en",
       "Message": "message",
       "OutputDataConfig": {
          "S3Uri": "s3://output bucket/ouput path"
       },
       "SubmitTime": timestamp,
       "TargetEventTypes": [
         "BANKRUPTCY",
         "EMPLOYMENT",
         "CORPORATE_ACQUISITION",
         "INVESTMENT_GENERAL",
         "CORPORATE_MERGER",
         "IPO",
         "RIGHTS_ISSUE",
         "SECONDARY_OFFERING",
         "SHELF_OFFERING",
         "TENDER_OFFERING",
         "STOCK_SPLIT"
  ]
    }
 ],
 "NextToken": "next token"
}
```

## Describe events using the AWS CLI<a name="describe-events"></a>

You can use the [DescribeEventsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DescribeEventsDetectionJob.html) operation to get the status of an existing job\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

```
aws comprehend describe-events-detection-job \
  --region region \
  --job-id job ID
```

You will get the following JSON in response:

```
{
 "EventsDetectionJobProperties": {
    "DataAccessRoleArn": "arn:aws:iam::account ID:role/data access role",
    "EndTime": timestamp,
    "InputDataConfig": {
       "InputFormat": "ONE_DOC_PER_LINE",
       "S3Uri": "S3Uri": "s3://input bucket/input path"
    },
    "JobId": "job ID",
    "JobName": "job name",
    "JobStatus": "job status",
    "LanguageCode": "en",
    "Message": "message",
    "OutputDataConfig": {
       "S3Uri": "s3://output bucket/output path"
    },
    "SubmitTime": timestamp,
    "TargetEventTypes": [
      "BANKRUPTCY",
      "EMPLOYMENT",
      "CORPORATE_ACQUISITION",
      "INVESTMENT_GENERAL",
      "CORPORATE_MERGER",
      "IPO",
      "RIGHTS_ISSUE",
      "SECONDARY_OFFERING",
      "SHELF_OFFERING",
      "TENDER_OFFERING",
      "STOCK_SPLIT"
  ]
 }
}
```

## Get events detection results<a name="async-events"></a>

The following is an example an output file from an analysis job that detected events in documents\. The format of the input is one document per line\. 

```
{"Entities": [{"Mentions": [{"BeginOffset": 12, "EndOffset": 27, "GroupScore": 1.0, "Score": 0.916355, "Text": "over a year ago", "Type": "DATE"}]}, {"Mentions": [{"BeginOffset": 33, "EndOffset": 39, "GroupScore": 1.0, "Score": 0.996603, "Text": "Amazon", "Type": "ORGANIZATION"}]}, {"Mentions": [{"BeginOffset": 66, "EndOffset": 77, "GroupScore": 1.0, "Score": 0.999283, "Text": "Whole Foods", "Type": "ORGANIZATION"}]}], "Events": [{"Arguments": [{"EntityIndex": 2, "Role": "INVESTEE", "Score": 0.999283}, {"EntityIndex": 0, "Role": "DATE", "Score": 0.916355}, {"EntityIndex": 1, "Role": "INVESTOR", "Score": 0.996603}], "Triggers": [{"BeginOffset": 373, "EndOffset": 380, "GroupScore": 0.999984, "Score": 0.999955, "Text": "acquire", "Type": "CORPORATE_ACQUISITION"}], "Type": "CORPORATE_ACQUISITION"}, {"Arguments": [{"EntityIndex": 2, "Role": "PARTICIPANT", "Score": 0.999283}], "Triggers": [{"BeginOffset": 115, "EndOffset": 123, "GroupScore": 1.0, "Score": 0.999967, "Text": "combined", "Type": "CORPORATE_MERGER"}], "Type": "CORPORATE_MERGER"}], "File": "doc.txt", "Line": 0}
```

For more information about events output file structure and supported event types, see [Events](how-events.md)\.