# Using Amazon S3 Object Lambda Access Points for Personally Identifiable Information \(PII\)<a name="using-access-points"></a>

Use Amazon S3 Object Lambda Access Points for personally identifiable information \(PII\) to configure how documents are retrieved from your Amazon S3 bucket\. You can control access to documents that contain PII and redact PII from documents\. For more information on how Amazon Comprehend can detect PII in your documents, see [Detect Personally Identifiable Information \(PII\)](how-pii.md)\. Amazon S3 Object Lambda Access Points use AWS Lambda functions to automatically transform the output of a standard Amazon S3 GET request\. For more information see, [Transforming objects with S3 Object Lambda](https://docs.aws.amazon.com/AmazonS3/latest/userguide/transforming-objects.html) in the *Amazon Simple Storage Service User Guide*\. 

When you create an Amazon S3 Object Lambda Access Point for PII, documents are processed using Amazon Comprehend Lambda functions to control access of documents that contain PII and redact PII from documents\.

When you create an Amazon S3 Object Lambda Access Point for PII, documents are processed using the following Amazon Comprehend Lambda functions:


+ `ComprehendPiiAccessControlS3ObjectLambda` \- Controls access to documents with PII stored in your S3 bucket\. For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiAccessControlS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiAccessControlS3ObjectLambda) function in the AWS Serverless Application Repository\. 
+ `ComprehendPiiRedactionS3ObjectLambda` \- Redacts PII from documents in your Amazon S3 bucket\. For more information about this Lambda function, sign in to the AWS Management Console to view the [ComprehendPiiRedactionS3ObjectLambda](https://console.aws.amazon.com/lambda/home#/create/app?applicationId=arn:aws:serverlessrepo:us-east-1:839782855223:applications/ComprehendPiiRedactionS3ObjectLambda) function in the AWS Serverless Application Repository\.

For information about how to deploy serverless applications from the AWS Serverless Application Repository, see [Deploying Applications](https://docs.aws.amazon.com/serverlessrepo/latest/devguide/serverlessrepo-consuming-applications.html) in the *AWS Serverless Application Repository Developer Guide*\.

**Topics**
+ [Controlling Access to Documents with Personally Identifiable Information \(PII\)](access-point-pii-control.md)
+ [Redacting Personally Identifiable Information \(PII\) from Documents](access-point-pii-redact.md)