# Creating a Custom Classifier \(Console\)<a name="getting-started-console-classifier"></a>

Create a custom document classifier to identify the categories of a set of documents\.

To train the classifier, you need a set of training documents\. You label these documents with the categories that you want the document classifier to recognize\. For more information on these training documents, see [Custom Classification](how-document-classification.md)\.

**To train a document classifier**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom Classification**\.

1. Choose **Train classifier**\.

1. Give the classifier a name\. The name must be unique within your account and current Region\.

1. Select the language of the training documents\. You can train a document classifier using any of the languages that work with Amazon Comprehend\. However, you can only train the classifier in one language\.

1. \(Optional\) If you want to encrypt the data in the storage volume while your training job is being processed, choose **Classifier encryption** and then choose whether to use a KMS key associated with your current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key ID under **KMS key ARN**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key Management Service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Training data**, choose which classifier mode to use\.
   + Multi\-class mode: Choose this option if the categories you are assigning to documents are mutually exclusive and you are training your classifier to assign one and only one label to each document\.
   + Multi\-label mode: Choose this option if multiple categories can applied to a document at the same time and you are training your classifier to assign one, many, all, or no label to each document\. 

1. If you chose **Multi\-label mode**, choose the character delimiter you want to use to separate labels when there are more than one label per line from **Delimiter for labels**\.

1. Enter the location of the Amazon S3 bucket that contains your training documents or navigate to it by choosing **Select folder**\. The IAM role you're using for access permissions for the training job must have reading permuissions for the S3 bucket\.

1. \(Optional\) If you want Amazon Comprehend to create a confusion matrix that provides metrics on how well the classifier performed during training, enter the location of an Amazon S3 bucket where it will be saved\. For more information, see [Confusion Matrix](conf-matrix.md)\.

   \(Optional\) If you choose to encrypt the output result from your training job, choose **Encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key alias for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.

1. Choose **Choose an existing IAM role**, and then choose an existing IAM role that has read permissions for the S3 bucket that contains your training documents\. Only roles that have a trust policy that begins with comprehend\.amazonaws\.com are valid\.

   If you don't already have an IAM role with these permissions, choose **Create an IAM role** to make one\. Choose the access permissions to grant this role, and then choose a name suffix to distinguish the role from IAM roles in your account\.
**Note**  
If the input documents are encrypted, the IAM role used must also have `kms:Decrypt` permission\. For more information, see [Permissions Required to Use KMS Encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnets\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your classification job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. \(Optional\) To add a tag to the custom classifier, enter a key\-value pair under **Tags**\. Choose **Add tag**\. To remove this pair before creating the classifier, choose **Remove tag**\. For more information, see [Tagging Custom Classifiers](class-tagging.md)\.

1. Choose **Create classifier**\.

The new classifier will then appear in the list, showing its status\. It will first show as `Submitted`\. It will then show `Training` for a classifier that is processing training documents, `Trained` for a classifier that is ready to use, and `In error` for a classifier that has an error\. You can click on a job to get more information about the classifier, including any error messages\.

![\[The custom classifier list.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/class-list.png)