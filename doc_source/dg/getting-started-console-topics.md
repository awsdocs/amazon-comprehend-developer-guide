# Creating a Topic Modeling Job Using the Console<a name="getting-started-console-topics"></a>

You can use the Amazon Comprehend console to create and manage asynchronous topic detection jobs\.

**To create a topic modeling job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Analysis Jobs** and then choose **Create**\.

1. Under **Job settings**, give the job a name\. The name must be unique within the region and account\.

1. For **Analysis Type**, choose **Topic Modeling**\. 

1. \(Optional\) If you choose to encrypt the data in the storage volume while your job is processed, choose **Job encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, for **KMS key ID**choose the key ID\.
   + If you are using a key associated with a different account, for **KMS key ARN** enter the ARN for the key ID\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key Management Service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Choose the data source to use\. You can use either sample data or you can analyze your own data stored in an Amazon S3 bucket\. 

   If you choose to use your own data, provide the following information:
   + **S3 data location** – An Amazon S3 data bucket that contains the documents to analyze\. You can choose the folder icon to browse to the location of your data\. The bucket must be in the same region as the API that you are calling\.
   + **Input format** – Optionally choose whether input data is contained in one document per file, or if there is one document per line in a file\.
   + **Number of topics** – The number of topics to return\.

1. \(Optional\) If you choose to encrypt the output result from your job, choose **Encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, for **KMS key ID** choose the key alias or ID\.
   + If you are using a key associated with a different account, for **KMS key ID** enter the ARN for the key alias or ID\.

1. In the **Choose an IAM role** section, either select an existing IAM role or create a new one\.
   + **Choose an existing IAM role** – Choose this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.
   + **Create a new IAM role** – Choose this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. For more information about the permissions given to the IAM role, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.
**Note**  
If the input documents are encrypted, the IAM role used must have `KMS:Decrypt` permission\. For more information, see [Permissions Required to Use KMS Encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your topic modeling job, the `DataAccessRole` that is used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.

The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. You can click on a job to get more information about the job, including any error messages\.