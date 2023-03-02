# Getting started with Amazon Comprehend<a name="getting-started"></a>

The following exercise uses the Amazon Comprehend console to create and run an asynchronous entity detection job\. This exercise assumes that you are familiar with Amazon Simple Storage Service \(Amazon S3\)\. For a simpler example, see [Real\-time analysis using the built\-in models](realtime-console-analysis.md)\.

**To create a entity detection job**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Analysis Jobs** and then choose **Create job**\.

1. Under **Job settings**, give the job a name\. The name must be unique within the Region and account\.

1. For **Analysis Type**, choose **Entities**\. 

1. For **Language**, choose the language of the input documents\. 

1. Under **Input data**, for **Data source**, choose **Example documents**\. The console sets **S3 location** to be the folder containing the public samples\.

1. Under **Output data**, in **S3 location**, paste the URL or folder location in Amazon S3 for the output files\.

1. Under **Access permissions** section, select **Create an IAM role**\. The console creates a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. 

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.

   The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. 

1. Choose the job to open the **Job details panel**\.

1. Under **Output**, in **Output data location** choose the link to open the Amazon S3 console\.

1. In the Amazon S3 console, choose **Download** and save the `output.tar.gz` file\.

1. Decompress the file and save it as a Json file\.

1. See [Entities](how-entities.md) for a description of the entity types and the fields for each detected entity\.