# Step 2: \(CLI Only\) Creating an IAM Role for Amazon Comprehend<a name="tutorial-reviews-create-role"></a>

This step is necessary only if you are using the AWS Command Line Interface \(AWS CLI\) to complete this tutorial\. If you are using the Amazon Comprehend console to run the analysis jobs, skip to [Step 3: Running Analysis Jobs on Documents in Amazon S3](tutorial-reviews-analysis.md)\.

To run analysis jobs, Amazon Comprehend requires access to the Amazon S3 bucket that contains the sample dataset and will contain the jobs' output\. IAM roles allow you to control the permissions of AWS services or users\. In this step, you create an IAM role for Amazon Comprehend\. Then, you create and attach to this role a resource\-based policy that grants Amazon Comprehend access to your S3 bucket\. By the end of this step, Amazon Comprehend will have the necessary permissions to access your input data, store your output, and run sentiment and entities analysis jobs\.

For more information about using IAM with Amazon Comprehend, see [Overview of Managing Access Permissions to Amazon Comprehend Resources](access-control-overview.md) and [Using Identity\-Based Policies \(IAM Policies\) for Amazon Comprehend](access-control-managing-permissions.md) in the *Amazon Comprehend User Guide*\.

**Topics**
+ [Prerequisites](#tutorial-reviews-create-role-prereqs)
+ [Create an IAM Role](#tutorial-reviews-create-role-trust-policy)
+ [Attach an IAM Policy to the IAM Role](#tutorial-reviews-create-role-policy)

## Prerequisites<a name="tutorial-reviews-create-role-prereqs"></a>

Before you begin, do the following:
+ Complete [Step 1: Adding Documents to Amazon S3](tutorial-reviews-add-docs.md)\.
+ Have a code or text editor to save JSON policies and keep track of your Amazon Resource Names \(ARNs\)\.

## Create an IAM Role<a name="tutorial-reviews-create-role-trust-policy"></a>

To access your Amazon Simple Storage Service \(Amazon S3\) bucket, Amazon Comprehend needs to assume an AWS Identity and Access Management \(IAM\) role\. The IAM role declares Amazon Comprehend as a trusted entity\. After Amazon Comprehend assumes the role and becomes a trusted entity, you can grant bucket access permissions to Amazon Comprehend\. In this step, you create a role that labels Amazon Comprehend as a trusted entity\. You can create a role with the AWS CLI or the Amazon Comprehend console\. To use the console, skip to [Step 3: Running Analysis Jobs on Documents in Amazon S3](tutorial-reviews-analysis.md)\.

The Amazon Comprehend console lets you select roles where the role name contains 'Comprehend' and the trust policy includes comprehend\.amazonaws\.com\. Configure your CLI\-created roles to meet these criteria if you want the console to display them\.



**To create an IAM role for Amazon Comprehend \(AWS CLI\)**

1. Save the following trust policy as a JSON document called `comprehend-trust-policy.json` in a code or text editor on your computer\. This trust policy declares Amazon Comprehend as a trusted entity and allows it to assume an IAM role\.

   ```
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Effect": "Allow",
         "Principal": {
           "Service": "comprehend.amazonaws.com"
         },
         "Action": "sts:AssumeRole"
       }
     ]
   }
   ```

1. To create the IAM role, run the following AWS CLI command\. The command creates an IAM role called `AmazonComprehendServiceRole-access-role` and attaches the trust policy to the role\. Replace `path/` with your local computer's path to the JSON document\.

   ```
   aws iam create-role --role-name AmazonComprehendServiceRole-access-role
   --assume-role-policy-document file://path/comprehend-trust-policy.json
   ```
**Tip**  
If you get an Error parsing parameter message, the path to your JSON trust policy file is probably incorrect\. Provide the relative path to the file based on your home directory\.

1. Copy the Amazon Resource Name \(ARN\) and save it in a text editor\. The ARN has a format similar to `arn:aws:iam::123456789012:role/AmazonComprehendServiceRole-access-role`\. You need this ARN to run Amazon Comprehend analysis jobs\.

## Attach an IAM Policy to the IAM Role<a name="tutorial-reviews-create-role-policy"></a>

To access your Amazon S3 bucket, Amazon Comprehend needs permissions to list, read, and write\. To give Amazon Comprehend the required permissions, create and attach an IAM policy to your IAM role\. The IAM policy allows Amazon Comprehend to retrieve the input data from your bucket and write analysis results to the bucket\. After creating the policy, you attach it to your IAM role\.

**To create an IAM policy \(AWS CLI\)**

1. Save the following policy locally as a JSON document called `comprehend-access-policy.json`\. It grants Amazon Comprehend access to the specified S3 bucket\.

   ```
   {
       "Version": "2012-10-17",
       "Statement": [
           {
               "Action": [
                   "s3:GetObject"
               ],
               "Resource": [
                   "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
               ],
               "Effect": "Allow"
           },
           {
               "Action": [
                   "s3:ListBucket"
               ],
               "Resource": [
                   "arn:aws:s3:::DOC-EXAMPLE-BUCKET"
               ],
               "Effect": "Allow"
           },
           {
               "Action": [
                   "s3:PutObject"
               ],
               "Resource": [
                   "arn:aws:s3:::DOC-EXAMPLE-BUCKET/*"
               ],
               "Effect": "Allow"
           }
       ]
   }
   ```

1. To create the S3 bucket access policy, run the following AWS CLI command\. Replace `path/` with your local computer's path to the JSON document\.

   ```
   aws iam create-policy --policy-name comprehend-access-policy
   --policy-document file://path/comprehend-access-policy.json
   ```

1. Copy the access policy ARN and save it in a text editor\. The ARN has a format similar to `arn:aws:iam::123456789012:policy/comprehend-access-policy`\. You need this ARN to attach your access policy to your IAM role\.

**To attach the IAM policy to your IAM role \(AWS CLI\)**
+ Run the following command\. Replace `policy-arn` with the access policy ARN that you copied in the previous step\.

  ```
  aws iam attach-role-policy --policy-arn policy-arn
  --role-name AmazonComprehendServiceRole-access-role
  ```

You now have an IAM role called `AmazonComprehendServiceRole-access-role` that has a trust policy for Amazon Comprehend and an access policy that grants Amazon Comprehend access to your S3 bucket\. You also have the ARN for the IAM role copied to a text editor\.