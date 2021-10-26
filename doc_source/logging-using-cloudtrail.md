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
+ [BatchDetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectDominantLanguage.html)
+ [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectEntities.html)
+ [BatchDetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectKeyPhrases.html)
+ [BatchDetectSentiment](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectSentiment.html)
+ [BatchDetectSyntax](https://docs.aws.amazon.com/comprehend/latest/dg/API_BatchDetectSyntax.html)
+ [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/dg/API_ClassifyDocument.html)
+ [CreateDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateDocumentClassifier.html)
+ [CreateEndpoint](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateEndpoint.html)
+ [CreateEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_CreateEntityRecognizer.html)
+ [DeleteDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_DeleteDocumentClassifier.html)
+ [DeleteEndpoint](https://docs.aws.amazon.com/comprehend/latest/dg/API_DeleteEndpoint.html)
+ [DeleteEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_DeleteEntityRecognizer.html)
+ [DescribeDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDocumentClassificationJob.html)
+ [DescribeDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDocumentClassifier.html) 
+ [DescribeDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeDominantLanguageDetectionJob.html) 
+ [DescribeEndpoint](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEndpoint.html)
+ [DescribeEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEntitiesDetectionJob.html) 
+ [DescribeEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeEntityRecognizer.html) 
+ [DescribeKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeKeyPhrasesDetectionJob.html) 
+ [DescribePiiEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribePiiEntitiesDetectionJob.html) 
+ [DescribeSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeSentimentDetectionJob.html) 
+ [DescribeTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_DescribeTopicsDetectionJob.html) 
+ [DetectDominantLanguage](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectDominantLanguage.html)
+ [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectEntities.html)
+ [DetectKeyPhrases](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectKeyPhrases.html)
+ [DetectPiiEntities](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectPiiEntities.html)
+ [DetectSentiment](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectSentiment.html)
+ [DetectSyntax](https://docs.aws.amazon.com/comprehend/latest/dg/API_DetectSyntax.html)
+ [ListDocumentClassificationJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDocumentClassificationJobs.html) 
+ [ListDocumentClassifiers](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDocumentClassifiers.html) 
+ [ListDominantLanguageDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListDominantLanguageDetectionJobs.html) 
+ [ListEndpoints](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEndpoints.html)
+ [ListEntitiesDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEntitiesDetectionJobs.html) 
+ [ListEntityRecognizers](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListEntityRecognizers.html) 
+ [ListKeyPhrasesDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListKeyPhrasesDetectionJobs.html) 
+ [ListPiiEntitiesDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListPiiEntitiesDetectionJobs.html) 
+ [ListSentimentDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListSentimentDetectionJobs.html) 
+ [ListTagsForResource](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListTagsForResource.html) 
+ [ListTopicsDetectionJobs](https://docs.aws.amazon.com/comprehend/latest/dg/API_ListTopicsDetectionJobs.html) 
+ [StartDocumentClassificationJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDocumentClassificationJob.html) 
+ [StartDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartDominantLanguageDetectionJob.html) 
+ [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartEntitiesDetectionJob.html) 
+ [StartKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartKeyPhrasesDetectionJob.html) 
+ [StartPiiEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartPiiEntitiesDetectionJob.html) 
+ [StartSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartSentimentDetectionJob.html)
+  [StartTopicsDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StartTopicsDetectionJob.html) 
+ [StopDominantLanguageDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopDominantLanguageDetectionJob.html) 
+ [StopEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopEntitiesDetectionJob.html) 
+ [StopKeyPhrasesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopKeyPhrasesDetectionJob.html) 
+ [StopPiiEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopPiiEntitiesDetectionJob.html) 
+ [StopSentimentDetectionJob](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopSentimentDetectionJob.html) 
+ [StopTrainingDocumentClassifier](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopTrainingDocumentClassifier.html) 
+ [StopTrainingEntityRecognizer](https://docs.aws.amazon.com/comprehend/latest/dg/API_StopTrainingEntityRecognizer.html)
+ [TagResource](https://docs.aws.amazon.com/comprehend/latest/dg/API_TagResource.html)
+ [UntagResource](https://docs.aws.amazon.com/comprehend/latest/dg/API_UntagResource.html)
+ [UpdateEndpoint](https://docs.aws.amazon.com/comprehend/latest/dg/API_UpdateEndpoint.html)

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
            "type": "AssumedRole”,`
            "principalId": "AROAICFHPEXAMPLE:kapil”,
            "arn": "arn:aws:sts::12345678910:assumed-role/UserRole/kapil”,
            "accountId": "12345678910",
            "accessKeyId": "ASIA3VZEXAMPLE”,
            "sessionContext": {
                "sessionIssuer": {
                    "type": "Role",
                    "principalId": "AROAICFHPEXAMPLE",
                    "arn": "arn:aws:iam::12345678910:role/UserRole",
                    "accountId": "12345678910",
                    "userName": "UserRole"
                },
                "webIdFederationData": {},
                "attributes": {
                    "mfaAuthenticated": "false",
                    "creationDate": "2020-04-29T15:46:04Z"
                }
            }
        },
    "eventTime": "2020-04-29T17:57:06Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "ListKeyPhrasesDetectionJobs",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "3.22.248.29",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "requestParameters": {
        "filter": {
            "submitTimeAfter": "Apr 29, 2020 5:54:04 PM"
        }
    },
    "responseElements": null,
    "requestID": "59bee2bc-e45c-436e-aae7-493af0328a8c",
    "eventID": "eabb7b59-edf3-44c8-8833-416bbdb16eae",
    "readOnly": true,
    "eventType": "AwsApiCall",
    "recipientAccountId": "802699264198"
}
```

The following example shows a CloudTrail log entry that demonstrates the `StartKeyPhrasesDetectionJob` action\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole”,`
        "principalId": "AROAICFHPEXAMPLE:kapil”,
        "arn": "arn:aws:sts::12345678910:assumed-role/UserRole/kapil”,
        "accountId": "12345678910",
        "accessKeyId": "ASIA3VZEXAMPLE”,
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "AROAICFHPEXAMPLE",
                "arn": "arn:aws:iam::12345678910:role/UserRole",
                "accountId": "12345678910",
                "userName": "UserRole"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-04-29T15:46:04Z"
            }
        }
    },
    "eventTime": "2020-04-29T16:42:39Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "StartKeyPhrasesDetectionJob",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "3.20.236.234",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "requestParameters": {
        "inputDataConfig": {
            "s3Uri": "s3://dataset-prod-us-east-2/ONE_DOC_PER_LINE/KP/FOUR_KB",
            "inputFormat": "ONE_DOC_PER_LINE"
        },
        "outputDataConfig": {
            "s3Uri": "s3://datasets3bucke-y6icltvagurj/JSON/00f706b3-6d84-4b09-bea3-88084f9cb6b0",
            "kmsKeyId": "arn:aws:kms:us-east-2:12345678910:key/2e107fe3-6ab3-4bab-90ab-966e85b14678"
        },
        "dataAccessRoleArn": "arn:aws:iam::12345678910:role/DataAccessRoleXYZ",
        "languageCode": "en",
        "clientRequestToken": "d9e4f777-8b4e-4249-8ebb-b7495acb800b",
        "volumeKmsKeyId": "arn:aws:kms:us-east-2:12345678910:key/7b9b8aff-c459-4d20-bb39-64d6e3756e85"
    },
    "responseElements": {
        "jobId": "2102905798f0d44a04da91fbd12ed60e",
        "jobStatus": "SUBMITTED"
    },
    "requestID": "f202914c-f5cf-4f2d-a4c7-5f30d101fe19",
    "eventID": "692e3a17-40a2-491a-a4ce-a275c4c4ce76",
    "readOnly": false,
    "resources": [
        {
            "accountId": "12345678910",
            "type": "AWS::KMS::Key",
            "ARN": "arn:aws:kms:us-east-2:12345678910:key/2e107fe3-6ab3-4bab-90ab-966e85b14678"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::KMS::Key",
            "ARN": "arn:aws:kms:us-east-2:12345678910:key/7b9b8aff-c459-4d20-bb39-64d6e3756e85"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::S3::Object",
            "ARN": "s3://dataset-prod-us-east-2/ONE_DOC_PER_LINE/KP/FOUR_KB"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::S3::Object",
            "ARN": "s3://datasets3bucke-y6icltvagurj/JSON/00f706b3-6d84-4b09-bea3-88084f9cb6b0"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::IAM::Role",
            "ARN": "arn:aws:iam::12345678910:role/DataAccessRoleXYZ"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "12345678910"
}
```

The following example shows a CloudTrail log entry that demonstrates the `DescribeDocumentClassifier` action\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "AROAICFHPEXAMPLE:SomeServiceCa-CheckAsyncJobStatusLambd-TICR23C65S42",
        "arn": "arn:aws:sts::12345678910:assumed-role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X/SomeServiceCa-CheckAsyncJobStatusLambd-TICR23C65S42",
        "accountId": "12345678910",
        "accessKeyId": "ASIA3VZEXAMPLE",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "AROAICFHPEXAMPLE",
                "arn": "arn:aws:iam::12345678910:role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X",
                "accountId": "12345678910",
                "userName": "SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-04-29T15:30:41Z"
            }
        }
    },
    "eventTime": "2020-04-29T17:02:44Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "DescribeDocumentClassifier",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "18.191.40.153",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "errorCode": "ResourceNotFoundException",
    "errorMessage": "RESOURCE_NOT_FOUND: Could not find specified resource.",
    "requestParameters": {
        "documentClassifierArn": "arn:aws:comprehend:us-east-2:12345678910:document-classifier/DocumentClassifier-FOUR-KB-MULTI-LABEL-1588162272420"
    },
    "responseElements": null,
    "requestID": "e5bf2476-a894-4204-af77-4a84857ff2f8",
    "eventID": "bc77875f-9fe5-4b65-8384-c9f82c392f46",
    "readOnly": true,
    "resources": [
        {
            "accountId": "12345678910",
            "type": "AWS::Comprehend::DocumentClassifier",
            "ARN": "arn:aws:comprehend:us-east-2:12345678910:document-classifier/DocumentClassifier-FOUR-KB-MULTI-LABEL-1588162272420"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "12345678910"
}
```

The following example shows a CloudTrail log entry that demonstrates the `CreateDocumentClassifier` action\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "AROAICFHPEXAMPLE:SomeServiceCanary-StartAsyncJobLambda-1STGUG0X870YM",
        "arn": "arn:aws:sts::12345678910:assumed-role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X/SomeServiceCanary-StartAsyncJobLambda-1STGUG0X870YM",
        "accountId": "12345678910",
        "accessKeyId": "ASIA3VZEXAMPLE",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "AROAICFHPEXAMPLE",
                "arn": "arn:aws:iam::12345678910:role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X",
                "accountId": "12345678910",
                "userName": "SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-04-29T15:46:04Z"
            }
        }
    },
    "eventTime": "2020-04-29T17:01:33Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "CreateDocumentClassifier",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "3.20.236.234",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "requestParameters": {
        "documentClassifierName": "DocumentClassifier-FOUR-KB-MULTI-CLASS-1588179693504",
        "dataAccessRoleArn": "arn:aws:iam::12345678910:role/SomeServiceCanary-CMH-p-DataAccessRole-1DI9T5MJ973BK",
        "tags": [
            {
                "key": "CreationTag",
                "value": "TagValue"
            }
        ],
        "inputDataConfig": {
            "s3Uri": "s3://aws-deepinsight-async-canary-datasets-prod-us-east-2/ONE_DOC_PER_LINE/DOCUMENT_CLASSIFIER/FOUR_KB"
        },
        "clientRequestToken": "eb545dbf-52bd-474f-b0a2-b21010371e1b",
        "languageCode": "en",
        "volumeKmsKeyId": "arn:aws:kms:us-east-2:12345678910:key/7b9b8aff-c459-4d20-bb39-64d6e3756e85",
        "mode": "MULTI_CLASS"
    },
    "responseElements": {
        "documentClassifierArn": "arn:aws:comprehend:us-east-2:12345678910:document-classifier/DocumentClassifier-FOUR-KB-MULTI-CLASS-1588179693504"
    },
    "requestID": "20300c29-29bf-48fd-8275-e5a805ee8999",
    "eventID": "3444051d-3616-438f-b80e-a3be9bbc0341",
    "readOnly": false,
    "resources": [
        {
            "accountId": "12345678910",
            "type": "AWS::Comprehend::DocumentClassifier",
            "ARN": "arn:aws:comprehend:us-east-2:12345678910:document-classifier/DocumentClassifier-FOUR-KB-MULTI-CLASS-1588179693504"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::KMS::Key",
            "ARN": "arn:aws:kms:us-east-2:12345678910:key/7b9b8aff-c459-4d20-bb39-64d6e3756e85"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::S3::Object",
            "ARN": "s3://aws-deepinsight-async-canary-datasets-prod-us-east-2/ONE_DOC_PER_LINE/DOCUMENT_CLASSIFIER/FOUR_KB"
        },
        {
            "accountId": "12345678910",
            "type": "AWS::IAM::Role",
            "ARN": "arn:aws:iam::12345678910:role/SomeServiceCanary-CMH-p-DataAccessRole-1DI9T5MJ973BK"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "12345678910"
}
```

The following example shows a CloudTrail log entry that demonstrates the `DeleteEntityRecognizer` action\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "AROAICFHPEXAMPLE:SomeServiceCanary-StartAsyncJobLambda-1STGUG0X870YM",
        "arn": "arn:aws:sts::12345678910:assumed-role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X/SomeServiceCanary-StartAsyncJobLambda-1STGUG0X870YM",
        "accountId": "12345678910",
        "accessKeyId": "ASIA3VZEXAMPLE",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "AROAICFHPEXAMPLE",
                "arn": "arn:aws:iam::12345678910:role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X",
                "accountId": "12345678910",
                "userName": "SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-04-29T15:46:04Z"
            }
        }
    },
    "eventTime": "2020-04-29T17:01:13Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "DeleteEntityRecognizer",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "3.20.236.234",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "requestParameters": {
        "entityRecognizerArn": "arn:aws:comprehend:us-east-2:12345678910:entity-recognizer/EntityRecognizer-DOCS-2K-ONE-DOC-PER-LINE-1588161691587"
    },
    "responseElements": null,
    "requestID": "ab49a08d-3579-4f10-a62f-eb72e359e516",
    "eventID": "fb9860a1-b158-4764-a306-d19cfbace7fc",
    "readOnly": false,
    "resources": [
        {
            "accountId": "12345678910",
            "type": "AWS::Comprehend::EntityRecognizer",
            "ARN": "arn:aws:comprehend:us-east-2:12345678910:entity-recognizer/EntityRecognizer-DOCS-2K-ONE-DOC-PER-LINE-1588161691587"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "12345678910"
}
```

The following example shows a CloudTrail log entry that demonstrates the `ClassifyDocument` action\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "AssumedRole",
        "principalId": "AROAICFHPEXAMPLE:SomeServiceCa-ValidateEndpointOutputLa-C5F50672CNDK",
        "arn": "arn:aws:sts::12345678910:assumed-role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X/SomeServiceCa-ValidateEndpointOutputLa-C5F50672CNDK",
        "accountId": "12345678910",
        "accessKeyId": "ASIA3VZEXAMPLE",
        "sessionContext": {
            "sessionIssuer": {
                "type": "Role",
                "principalId": "AROAICFHPEXAMPLE",
                "arn": "arn:aws:iam::12345678910:role/SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X",
                "accountId": "12345678910",
                "userName": "SomeServiceCa-SomeLambdaR-ADLIAGB0VT9X"
            },
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "2020-04-29T16:15:11Z"
            }
        }
    },
    "eventTime": "2020-04-29T17:10:26Z",
    "eventSource": "comprehend.amazonaws.com",
    "eventName": "ClassifyDocument",
    "awsRegion": "us-east-2",
    "sourceIPAddress": "3.21.185.237",
    "userAgent": "aws-internal/3 aws-sdk-java/1.11.761 Linux/4.14.165-102.205.amzn2.x86_64 OpenJDK_64-Bit_Server_VM/25.201-b09 java/1.8.0_201 vendor/Oracle_Corporation, canary-generated exec-env/AWS_Lambda_java8",
    "requestParameters": {
        "endpointArn": "arn:aws:comprehend:us-east-2:12345678910:document-classifier-endpoint/canary86644"
    },
    "responseElements": null,
    "requestID": "fd916e66-caac-46c9-a1fc-81a0ef33e61b",
    "eventID": "535ca22b-b3a3-4c13-b2c5-bf51ab082794",
    "readOnly": true,
    "resources": [
        {
            "accountId": "12345678910",
            "type": "AWS::Comprehend::DocumentClassifierEndpoint",
            "ARN": "arn:aws:comprehend:us-east-2:12345678910:document-classifier-endpoint/canary86644"
        }
    ],
    "eventType": "AwsApiCall",
    "recipientAccountId": "12345678910"
}
```