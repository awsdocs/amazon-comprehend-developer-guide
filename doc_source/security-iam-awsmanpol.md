# AWS Managed Policies for Amazon Comprehend<a name="security-iam-awsmanpol"></a>



To add permissions to users, groups, and roles, it is easier to use AWS managed policies than to write policies yourself\. It takes time and expertise to [create IAM customer managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html) that provide your team with only the permissions they need\. To get started quickly, you can use our AWS managed policies\. These policies cover common use cases and are available in your AWS account\. For more information about AWS managed policies, see [AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies) in the *IAM User Guide*\.

AWS services maintain and update AWS managed policies\. You can't change the permissions in AWS managed policies\. Services occasionally add additional permissions to an AWS managed policy to support new features\. This type of update affects all identities \(users, groups, and roles\) where the policy is attached\. Services are most likely to update an AWS managed policy when a new feature is launched or when new operations become available\. Services do not remove permissions from an AWS managed policy, so policy updates won't break your existing permissions\.

Additionally, AWS supports managed policies for job functions that span multiple services\. For example, the **ReadOnlyAccess** AWS managed policy provides read\-only access to all AWS services and resources\. When a service launches a new feature, AWS adds read\-only permissions for new operations and resources\. For a list and descriptions of job function policies, see [AWS managed policies for job functions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_job-functions.html) in the *IAM User Guide*\.









## AWS managed policy: ComprehendFullAccess<a name="security-iam-awsmanpol-ComprehendFullAccess"></a>

This policy grants full access to Amazon Comprehend resources including running topic modeling jobs\. This policy also grants list and get permissions for Amazon S3 buckets and IAM roles\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "comprehend:*",
                "s3:ListAllMyBuckets",
                "s3:ListBucket",
                "s3:GetBucketLocation",
                "iam:ListRoles",
                "iam:GetRole"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## AWS managed policy: ComprehendReadOnly<a name="security-iam-awsmanpol-ComprehendReadOnly"></a>

This policy grants read\-only permissions to run all Amazon Comprehend actions **except** the following:
+  `StartDominantLanguageDetectionJob` 
+  `StartEntitiesDetectionJob`
+  `StartKeyPhrasesDetectionJob`
+  `StartSentimentDetectionJob`
+  `StartTopicsDetectionJob`

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Action": [
                "comprehend:DetectDominantLanguage",
                "comprehend:BatchDetectDominantLanguage",
                "comprehend:DetectEntities",
                "comprehend:BatchDetectEntities",
                "comprehend:DetectKeyPhrases",
                "comprehend:BatchDetectKeyPhrases",
                "comprehend:DetectPiiEntities",
                "comprehend:DetectSentiment",
                "comprehend:BatchDetectSentiment",
                "comprehend:DetectSyntax",
                "comprehend:BatchDetectSyntax",
                "comprehend:ClassifyDocument",
                "comprehend:ContainsPiiEntities",
                "comprehend:DescribeTopicsDetectionJob",
                "comprehend:ListTopicsDetectionJobs",
                "comprehend:DescribeDominantLanguageDetectionJob",
                "comprehend:ListDominantLanguageDetectionJobs",
                "comprehend:DescribeEntitiesDetectionJob",
                "comprehend:ListEntitiesDetectionJobs",
                "comprehend:DescribeKeyPhrasesDetectionJob",
                "comprehend:ListKeyPhrasesDetectionJobs",
                "comprehend:DescribePiiEntitiesDetectionJob",
                "comprehend:ListPiiEntitiesDetectionJobs",
                "comprehend:DescribeSentimentDetectionJob",
                "comprehend:ListSentimentDetectionJobs",
                "comprehend:DescribeDocumentClassifier",
                "comprehend:ListDocumentClassifiers",
                "comprehend:ListDocumentClassifierSummaries",
                "comprehend:DescribeDocumentClassificationJob",
                "comprehend:ListDocumentClassificationJobs",
                "comprehend:DescribeEntityRecognizer",
                "comprehend:ListEntityRecognizers",
                "comprehend:ListEntityRecognizerSummaries",
                "comprehend:ListTagsForResource",
                "comprehend:DescribeEndpoint",
                "comprehend:ListEndpoints"
            ],
            "Effect": "Allow",
            "Resource": "*"
        }
    ]
}
```

## Amazon Comprehend updates to AWS managed policies<a name="security-iam-awsmanpol-updates"></a>



View details about updates to AWS managed policies for Amazon Comprehend since this service began tracking these changes\. For automatic alerts about changes to this page, subscribe to the RSS feed on the Amazon Comprehend [Document history](https://docs.aws.amazon.com/comprehend/latest/dg/doc-history.html) page\.




| Change | Description | Date | 
| --- | --- | --- | 
|  [ComprehendReadOnly](#security-iam-awsmanpol-ComprehendReadOnly) – Update to an existing policy  |  Amazon Comprehend added new permissions to allow the `ListDocumentClassifierSummaries` and `ListEntityRecognizerSummaries`action to the ComprehendReadOnly policy  | September 21, 2021 | 
|  [ComprehendReadOnly](#security-iam-awsmanpol-ComprehendReadOnly) – Update to an existing policy  | Amazon Comprehend added new permissions to allow the ContainsPIIEntities action to the ComprehendReadOnly policy | March 26, 2021 | 
|  Amazon Comprehend started tracking changes  |  Amazon Comprehend started tracking changes for its AWS managed policies\.  | March 1, 2021 | 