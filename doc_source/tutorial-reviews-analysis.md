# Step 3: Running analysis jobs on documents in Amazon S3<a name="tutorial-reviews-analysis"></a>

After storing the data in Amazon S3, you can begin running Amazon Comprehend analysis jobs\. A *sentiment* analysis job determines the overall mood of a document \(positive, negative, neutral, or mixed\)\. An *entities* analysis job extracts the names of real\-world objects from a document\. These objects include people, places, titles, events, dates, quantities, products, and organizations\. In this step, you run two Amazon Comprehend analysis jobs to extract the sentiment and entities from the sample dataset\.

**Topics**
+ [Prerequisites](#tutorial-reviews-analysis-prereqs)
+ [Analyze sentiment and entities](#tutorial-reviews-analysis-jobs)

## Prerequisites<a name="tutorial-reviews-analysis-prereqs"></a>

Before you begin, do the following:
+ Complete [Step 1: Adding documents to Amazon S3](tutorial-reviews-add-docs.md)\.
+ \(Optional\) If you are using the AWS CLI, complete [Step 2: \(CLI only\) creating an IAM role for Amazon Comprehend](tutorial-reviews-create-role.md) and have your IAM role ARN ready\.

## Analyze sentiment and entities<a name="tutorial-reviews-analysis-jobs"></a>

The first job you run analyzes the sentiment of each customer review in the sample dataset\. The second job extracts the entities in each customer review\. You can perform Amazon Comprehend analysis jobs either using the Amazon Comprehend console or the AWS CLI\. 

**Tip**  
Make sure that you are in an AWS Region that supports Amazon Comprehend\. For more information, see the [Region table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) in the *Global Infrastructure Guide*\.

### Analyze sentiments and entities \(console\)<a name="tutorial-reviews-analysis-jobs-console"></a>

When using the Amazon Comprehend console, you create one job at a time\. You need to repeat the following steps in order to run both a sentiment and an entities analysis job\. Note that for the first job, you create an IAM role, but for the second job, you can reuse the first job's IAM role\. You can reuse the IAM role as long as you use the same S3 bucket and folders\.

**To run sentiment and entities analysis jobs \(console\)**

1. Ensure that you're in the same Region in which you created your Amazon Simple Storage Service \(Amazon S3\) bucket\. If you're in another Region, in the navigation bar, choose the AWS Region where you created your S3 bucket from the **Region selector**\.

1. Open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. Choose **Launch Amazon Comprehend**\.

1. In the navigation pane, choose **Analysis jobs**\.

1. Choose **Create job**\.

1. In the **Job settings** section, do the following:

   1. For **Name**, enter `reviews-sentiment-analysis`\.

   1. For **Analysis type**, choose **Sentiment**\.

   1. For **Language**, choose **English**\.

   1. Leave the **Job encryption** setting as disabled\.

1. In the **Input data** section, do the following:

   1. For **Data source**, choose **My documents**\.

   1. For **S3 location**, choose **Browse S3** and then choose your bucket from the list of buckets\.

   1. In your S3 bucket, for **Objects**, choose your `input` folder\.

   1. In the `input` folder, choose the sample dataset `amazon-reviews.csv` and then choose **Choose**\.

   1. For **Input format**, choose **One document per line**\.

1. In the **Output data** section, do the following:

   1. For **S3 location**, choose **Browse S3** and then choose your bucket from the list of buckets\.

   1. In your S3 bucket, for **Objects**, choose the `output` folder and then choose **Choose**\.

   1. Leave **Encryption** turned off\.

1. In the **Access permissions** section, do the following:

   1. For **IAM role**, choose **Create an IAM role**\.

   1. For **Permissions to access**, choose **Input and Output S3 buckets**\.

   1. For **Name suffix**, enter `comprehend-access-role`\. This role provides access to your Amazon S3 bucket\.

1. Choose **Create job**\.

1. Repeat steps 1\-10 to create an entities analysis job\. Make the following changes:

   1. In **Job settings**, for **Name**, enter `reviews-entities-analysis`\.

   1. In **Job settings**, for **Analysis type**, choose **Entities**\.

   1. In **Access permissions**, choose **Use an existing IAM role**\. For **Role name**, choose `AmazonComprehendServiceRole-comprehend-access-role` \(this is the same role you created for the sentiment job\)\.

### Analyze sentiments and entities \(AWS CLI\)<a name="tutorial-reviews-analysis-jobs-cli"></a>

You use the `start-sentiment-detection-job` and the `start-entities-detection-job` commands to run sentiment and entities analysis jobs\. After you run each command, the AWS CLI shows a JSON object with a `JobId` value that allows you to access details about the job, including the output S3 location\.

**To run sentiment and entities analysis jobs \(AWS CLI\)**

1. Start a sentiment analysis job by running the following command in the AWS CLI\. Replace `arn:aws:iam::123456789012:role/comprehend-access-role` with the IAM role ARN that you previously copied to a text editor\. If your default AWS CLI Region differs from the Region in which you created your Amazon S3 bucket, include the `--region` parameter and replace `us-east-1` with the Region where your bucket resides\.

   ```
   aws comprehend start-sentiment-detection-job 
   --input-data-config S3Uri=s3://DOC-EXAMPLE-BUCKET/input/
   --output-data-config S3Uri=s3://DOC-EXAMPLE-BUCKET/output/ 
   --data-access-role-arn arn:aws:iam::123456789012:role/comprehend-access-role
   --job-name reviews-sentiment-analysis
   --language-code en
   [--region us-east-1]
   ```

1. After you submit the job, copy the `JobId` and save it to a text editor\. You will need the `JobId` to find the output files from the analysis job\.

1. Start an entities analysis job by running the following command\.

   ```
   aws comprehend start-entities-detection-job 
   --input-data-config S3Uri=s3://DOC-EXAMPLE-BUCKET/input/
   --output-data-config S3Uri=s3://DOC-EXAMPLE-BUCKET/output/ 
   --data-access-role-arn arn:aws:iam::123456789012:role/comprehend-access-role
   --job-name reviews-entities-analysis
   --language-code en
   [--region us-east-1]
   ```

1. After you submit the job, copy the `JobId` and save it to a text editor\.

1. Check the status of your jobs\. You can view the progress of a job by tracking its `JobId`\.

   To track the progress of your sentiment analysis job, run the following command\. Replace `sentiment-job-id` with the `JobId` that you copied after running your sentiment analysis\.

   ```
   aws comprehend describe-sentiment-detection-job
   --job-id sentiment-job-id
   ```

   To track your entities analysis job, run the following command\. Replace `entities-job-id` with the `JobId` that you copied after running your entities analysis\.

   ```
   aws comprehend describe-entities-detection-job
   --job-id entities-job-id
   ```

   It takes several minutes for the `JobStatus` to show as `COMPLETED`\.

You have completed sentiment and entities analysis jobs\. Both of the jobs should be completed before you move on to the next step\. It can take several minutes for the jobs to finish\.