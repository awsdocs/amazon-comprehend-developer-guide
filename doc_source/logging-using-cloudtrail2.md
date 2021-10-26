# Logging Amazon Comprehend Medical API Calls by Using AWS CloudTrail<a name="logging-using-cloudtrail2"></a>

Amazon Comprehend Medical is integrated with AWS CloudTrail\. CloudTrail is a service that provides a record of actions taken by a user, role, or an AWS service from within Amazon Comprehend Medical\. CloudTrail captures all API calls for Amazon Comprehend Medical as events\. The calls captured include calls from the Amazon Comprehend Medical console and code calls to the Amazon Comprehend Medical API operations\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon S3 bucket, including events for Amazon Comprehend Medical\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine several things such as:
+ The request that was made to Amazon Comprehend Medical
+ The IP address from which the request was made
+ Who made the request
+ When the request was made
+ Other details

To learn more about CloudTrail, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

## Amazon Comprehend Medical Information in CloudTrail<a name="service-name-info-in-cloudtrail2"></a>

CloudTrail is enabled on your AWS account when you create the account\. When activity occurs in Amazon Comprehend Medical, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for Amazon Comprehend Medical, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

All Amazon Comprehend Medical actions are logged by CloudTrail and are documented in the [Amazon Comprehend Medical API Reference](https://docs.aws.amazon.com/comprehend/latest/dg/API_Operations_AWS_Comprehend_Medical.html)\. For example, calls to the `DetectEntitiesV2`, `DetectPHI` and `ListEntitiesDetectionV2Jobs` actions generate entries in the CloudTrail log files\. 

Every event or log entry contains information about who generated the request\. The identity information helps you determine the following: 
+ Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials\.
+ Whether the request was made with temporary security credentials for a role or federated user\.
+ Whether the request was made by another AWS service\.

For more information, see the [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)\.

## Understanding Amazon Comprehend Medical Log File Entries<a name="understanding-service-name-entries2"></a>

A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source\. The event includes information about the requested action, such as the date and time or request parameters\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\. 

The following example shows a CloudTrail log entry that demonstrates the `DetectEntities` action\.

```
                {
        "eventVersion": "1.05",
        "userIdentity": {
            "type": "IAMUser",
            "principalId": "AIDACKCEVSQ6C2EXAMPLE",
            "arn": "arn:aws:iam::123456789012:user/Mateo_Jackson",
            "accountId": "123456789012",
            "accessKeyId": "ASIAXHKUFODNN8EXAMPLE",
            "sessionContext": {
                "sessionIssuer": {
                    "type": "Role",
                    "principalId": "AIDACKCEVSQ6C2EXAMPLE",
                    "arn": "arn:aws:iam::123456789012:user/Mateo_Jackson",
                    "accountId": "123456789012",
                    "userName": "Mateo_Jackson"
                },
                "webIdFederationData": {},
                "attributes": {
                    "mfaAuthenticated": "false",
                    "creationDate": "2019-09-27T20:07:27Z"
                }
            }
        },
        "eventTime": "2019-09-27T20:10:26Z",
        "eventSource": "comprehend.amazonaws.com",
        "eventName": "DetectEntities",
        "awsRegion": "us-east-1",
        "sourceIPAddress": "702.21.198.166",
        "userAgent": "aws-internal/3 aws-sdk-java/1.11.590 Linux/4.9.184-0.1.ac.235.83.329.metal1.x86_64 OpenJDK_64-Bit_Server_VM/25.212-b03 java/1.8.0_212 vendor/Oracle_Corporation",
        "requestParameters": null,
        "responseElements": null,
        "requestID": "8d85f2ec-EXAMPLE",
        "eventID": "ae9be9b1-EXAMPLE",
        "eventType": "AwsApiCall",
        "recipientAccountId": "123456789012"
    }
```