# Logging Amazon Comprehend API Calls with AWS CloudTrail<a name="logging-using-cloudtrail"></a>

Amazon Comprehend is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Amazon Comprehend\. CloudTrail captures API calls for Amazon Comprehend as events\. The calls captured include calls from the Amazon Comprehend console and code calls to the Amazon Comprehend API operations\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket, including events for Amazon Comprehend\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine the request that was made to Amazon Comprehend, the IP address from which the request was made, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, including how to configure and enable it, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## Amazon Comprehend Information in CloudTrail<a name="service-name-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in Amazon Comprehend, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for Amazon Comprehend, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

Amazon Comprehend supports logging the following actions as events in CloudTrail log files:
+ [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateDocumentClassifier.html)
+ [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateEntityRecognizer.html)
+ [DeleteDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_DeleteDocumentClassifier.html)
+ [DeleteEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_DeleteEntityRecognizer.html)
+ [DescribeDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDocumentClassificationJob.html)
+ [DescribeDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDocumentClassifier.html) 
+ [DescribeDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDominantLanguageDetectionJob.html) 
+ [DescribeEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEntitiesDetectionJob.html) 
+ [DescribeEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEntityRecognizer.html) 
+ [DescribeKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeKeyPhrasesDetectionJob.html) 
+ [DescribeSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeSentimentDetectionJob.html) 
+ [DescribeTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeTopicsDetectionJob.html) 
+ [ListDocumentClassificationJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDocumentClassificationJobs.html) 
+ [ListDocumentClassifiers](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDocumentClassifiers.html) 
+ [ListDominantLanguageDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDominantLanguageDetectionJobs.html) 
+ [ListEntitiesDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEntitiesDetectionJobs.html) 
+ [ListEntityRecognizers](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEntityRecognizers.html) 
+ [ListKeyPhrasesDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListKeyPhrasesDetectionJobs.html) 
+ [ListSentimentDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListSentimentDetectionJobs.html) 
+ [ListTopicsDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListTopicsDetectionJobs.html) 
+ [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDocumentClassificationJob.html) 
+ [StartDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDominantLanguageDetectionJob.html) 
+ [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartEntitiesDetectionJob.html) 
+ [StartKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartKeyPhrasesDetectionJob.html) 
+ [StartSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartSentimentDetectionJob.html)
+  [StartTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartTopicsDetectionJob.html) 
+ [StopDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopDominantLanguageDetectionJob.html) 
+ [StopEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopEntitiesDetectionJob.html) 
+ [StopKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopKeyPhrasesDetectionJob.html) 
+ [StopSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopSentimentDetectionJob.html) 
+ [StopTrainingDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopTrainingDocumentClassifier.html) 
+ [StopTrainingEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopTrainingEntityRecognizer.html)

Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+ Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials\.
+ Whether the request was made with temporary security credentials for a role or federated user\.
+ Whether the request was made by another AWS service\.

For more information, see the [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

## Examples: Amazon Comprehend Log File Entries<a name="understanding-service-name-entries"></a>

 A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\.

The following example shows a CloudTrail log entry that demonstrates the `ListKeyPhrasesDetectionJobs` action\.

```
{
            "eventVersion": "1.05",
            "userIdentity": {
                "type": "IAMUser",
                "principalId": "AIDACKCEVSQ6C2EXAMPLE",
                "arn": "arn:aws:iam::123456789012:user/Mateo_Jackson",
                "accountId": "123456789012",
                "accessKeyId": "AKIAIOSFODNN7EXAMPLE",
                "userName": "Mateo_Jackson"
            },
            "eventTime": "2019-01-01T01:21:23Z",
            "eventSource": "comprehend.amazonaws.com",
            "eventName": "ListKeyPhrasesDetectionJobs",
            "awsRegion": "us-west-2",
            "sourceIPAddress": "203.0.113.176",
            "userAgent": "aws-sdk-java/1.11.465 Linux/4.9.124-0.1.ac.198.71.329.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.192-b12 java/1.8.0_192",
            "requestParameters": {
                "nextToken": "uVuYaEXAMPLE",
                "filter": {
                    "submitTimeAfter": "Sep 14, 2018 8:05:13 PM"
                },
                "maxResults": 500
            },
            "responseElements": null,
            "requestID": "8d85f2ec-EXAMPLE",
            "eventID": "ae9be9b1-EXAMPLE",
            "eventType": "AwsApiCall",
            "recipientAccountId": "123456789012"
}
```

The following example shows a CloudTrail log entry that demonstrates the `StartKeyPhrasesDetectionJob` action\.

```
{
            "eventVersion": "1.05",
            "userIdentity": {
                "type": "IAMUser",
                "principalId": "AIDACKCEVSQ6C2EXAMPLE",
                "arn": "arn:aws:iam::123456789012:user/Li_Juan",
                "accountId": "123456789012",
                "accessKeyId": "AKIAI44QH8DHBEXAMPLE",
                "userName": "Li_Juan"
            },
            "eventTime": "2019-01-01T01:21:24Z",
            "eventSource": "comprehend.amazonaws.com",
            "eventName": "StartKeyPhrasesDetectionJob",
            "awsRegion": "us-west-2",
            "sourceIPAddress": "203.0.113.171",
            "userAgent": "aws-sdk-java/1.11.465 Linux/4.9.124-0.1.ac.198.71.329.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.192-b12 java/1.8.0_192",
            "requestParameters": {
                "dataAccessRoleArn": "arn:aws:iam::123456789012:role/S3AccessRole",
                "outputDataConfig": {
                    "s3Uri": "s3://admin-created/outputObjectPrefix"
                },
                "clientRequestToken": "f4d145f5-EXAMPLE",
                "languageCode": "en",
                "inputDataConfig": {
                    "s3Uri": "s3://admin-created/keyphrase/en/ONE_DOC_PER_LINE",
                    "inputFormat": "ONE_DOC_PER_LINE"
                },
                "jobName": "startKeyPhrasesDetectionJob_SubmitsExactlyOneRequest_WhenInputParametersSame:start-job-requests-with-same-idempotency-token:2019_01_01_00_35-fc293446-EXAMPLE"
            },
            "responseElements": {
                "jobStatus": "SUBMITTED",
                "jobId": "8954c07fEXAMPLE"
            },
            "requestID": "8db25a1f-EXAMPLE",
            "eventID": "0bbb5d6a-EXAMPLE",
            "eventType": "AwsApiCall",
            "recipientAccountId": "123456789012"
}
```