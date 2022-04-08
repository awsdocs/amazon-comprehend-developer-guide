# Getting started with Amazon Comprehend<a name="getting-started"></a>

The following exercise uses the Amazon Comprehend console to create and run an asynchronous entity detection job\.

**To create a entity detection job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Analysis Jobs** and then choose **Create job**\.

1. Under **Job settings**, give the job a name\. The name must be unique within the region and account\.

1. For **Analysis Type**, choose **Entities**\. 

1. Under **Input data**, for **Data source**, choose **Example documents**\. The console sets the S3 location to be the folder containing the public samples\.

1. In the **Choose an IAM role** section, select **Create a new IAM role**\. The console creates a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. 

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.

   The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. 

1. Choose the job to open the **Job details panel**\.

1. Under **Output**, in **Output data location** choose the link to open the Amazon S3 console\.

1. In the Amazon S3 console, choose **Download** and save the `output.tar.gz` file\.

1. Decompress the file and save it as a Json file\.

1. See [Entities](how-entities.md) for a description of the entity types and the fields for each detected entity\.