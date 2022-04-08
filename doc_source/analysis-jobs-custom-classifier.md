# Analysis jobs for custom classification \(console\)<a name="analysis-jobs-custom-classifier"></a>

After you create and train a [custom document classifier](), you can use it to run custom classifier jobs\.

**To create a custom classification job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Analysis jobs** and then choose **Create job**\.

1. Give the classification job a name\. The name must be unique your account and current Region\.

1. Under **Analysis type**, choose **Custom classification**\.

1. From **Select classifier**, choose the custom classifier to use\.

1. \(Optional\) If you choose to encrypt the data in the storage volume while your classification job is processed, choose **Job encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key ID under **KMS key ARN**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key management service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Input data**, enter the location of the Amazon S3 bucket that contains your input documents or navigate to it by choosing **Browse S3**\. This bucket must be in the same region as the API that you are calling\. The IAM role you're using for access permissions for the classification job must have reading permissions for the S3 bucket\.

1. \(Optional\) Choose the format of the documents to be classified under **Input format**\. These can be one document per file, or one document per line in a single file\.

1. Under **Output data**, enter the location of the Amazon S3 bucket where Amazon Comprehend should write the job's output data or navigate to it by choosing **Browse S3**\. This bucket must be in the same region as the API that you are calling\. The IAM role you're using for access permissions for the classification job must have write permissions for the S3 bucket\.

1. \(Optional\) If you choose to encrypt the output result from your job, choose **Encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key alias or ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your classification job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the output bucket are accessed\.

1. Choose **Create job** to create the document classification job\.