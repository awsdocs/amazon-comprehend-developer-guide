# Creating a Topic Modeling Job Using the Console<a name="getting-started-console-topics"></a>

You can use the Amazon Comprehend console to create and manage asynchronous topic detection jobs\.

**To Create a Topic Detection Job**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console\.

1. From the left menu, choose **Topic Modeling** and then choose **Create**\.

1. Choose the data source to use\. You can use either sample data or you can analyze your own data stored in an Amazon S3 bucket\. If you use the sample dataset, the topic modeling job analyzes text from this collection of articles: [https://s3\.amazonaws\.com/public\-sample\-attributions/Attributions\.txt](https://s3.amazonaws.com/public-sample-attributions/Attributions.txt)

1. If you chose to use your own data, provide the following information in the **Select input data** section:

   + **S3 data location** – an Amazon S3 data bucket that contains the documents to analyze\. You can choose the folder icon to browse to the location of your data\. The bucket must be in the same region as the API that you are calling\.

   + **Input format** – Choose whether in input data is contained in one document per file, or if there is one document per line in a file\.

   + **Number of topics** – The number of topics to return\.

   + **Job name** – a name that identifies the particular job\.

1. In the **Select output location** section, provide the following:

   + **S3 data location** – an Amazon S3 data bucket where the results of the analysis will be written\. The bucket must be in the same region as the API that your are calling\.

1. In the **Select an IAM role** section, either select an existing IAM role or create a new one\.

   + **Select an existing IAM role** – Select this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.

   + **Create a new IAM role** – Select this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. For more information about the permissions given to the IAM role, see [Role\-Based Permissions Required for Topic Detection](access-control-managing-permissions.md#auth-role-permissions)\.

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-60.png)

The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. You can click on a job to get more information about the job, including any error messages\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-70.png)