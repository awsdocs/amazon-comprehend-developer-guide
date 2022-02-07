# Detecting Events<a name="get-started-api-events"></a>

To detect events in a document set, use the [StartEventsDetectionJob](API_StartEventsDetectionJob.md) to start an asynchronous job\.

## Before You Start<a name="events-before"></a>

Before you start, make sure that you have:
+ **Input and output buckets**—Identify the Amazon S3 buckets that you want to use for input and output\. The buckets must be in the same region as the API that you are calling\.
+ **IAM service role**—You must have an IAM service role with permission to access your input and output buckets\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## Detecting Events Using the AWS Command Line Interface<a name="events-cli"></a>

The following example demonstrates using the [StartEventsDetectionJob](API_StartEventsDetectionJob.md) operation with the AWS CLI

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

Use the [ListEventsDetectionJobs](API_ListEventsDetectionJobs.md) operation to see a list of the events detection jobs that you have submitted\. The list includes information about the input and output locations that you used as well as the status of each of the detection jobs\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

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

You can use the [DescribeEventsDetectionJob](API_DescribeEventsDetectionJob.md) operation to get the status of an existing job\. The example is formatted for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\.

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