# Train custom classifiers \(console\)<a name="create-custom-classifier-console"></a>

You can create and train a custom classifier using the console, and then use the custom classifier to analyze your documents\.

To train a custom classifier, you need a set of training documents\. You label these documents with the categories that you want the document classifier to recognize\. For information about preparing your training documents, see [Preparing training data](prep-classifier-data.md)\.



**To create and train a document classifier**

1. Sign in to the [console](https://console.aws.amazon.com/comprehend/)\.

1. From the left menu, choose **Customization** and then choose **Custom Classification**\.

1. Choose **Create new model**\.

1. Give the classifier a name\. The name must be unique within your account and current Region\.

1. Select the language of the training documents\. You can train a document classifier using any of the languages that work with Amazon Comprehend\. However, you can only train the classifier in one language\. To learn more, see [Languages Supported by Amazon Comprehend\.](supported-languages.md) 

1. \(Optional\) If you want to encrypt the data in the storage volume while your training job is being processed, choose **Classifier encryption** and then choose whether to use a KMS key associated with your current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key ID under **KMS key ARN**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key management service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Data specifications**, choose which classifier mode to use\.
   + **Single\-label mode:** Choose this option if the categories you are assigning to documents are mutually exclusive and you are training your classifier to assign one and only one label to each document\.
   + **Multi\-label mode:** Choose this option if multiple categories can applied to a document at the same time and you are training your classifier to assign one, many, all, or no label to each document\. 

1. If you chose **Multi\-label mode**, choose the character delimiter you want to use to separate labels when there are more than one label per line from **Delimiter for labels**\.

1. Under **Data format**, choose the format of your training documents:
   + **CSV file** — A two\-column CSV file, where labels are provided in the first column, and documents are provided in the second\.
   + **Augmented manifest** — A labeled dataset that is produced by Amazon SageMaker Ground Truth\. This file is in JSON lines format\. Each line is a complete JSON object that contains a training document and its associated labels\.

   For more information about these formats, and for examples, see [Preparing training data](prep-classifier-data.md)\.

1. Under **Training dataset**, enter the location of the Amazon S3 bucket that contains your training documents or navigate to it by choosing **Select folder**\. The IAM role you're using for access permissions for the training job must have reading permissions for the S3 bucket\. 

1. Under **Test dataset** select how you want to evaluate the performance of your trained model \- you can do this for both annotations and entity list training types\.
   + **Autosplit**: Autosplit automatically selects 10% of your provided training data to use as testing data 
   + \(Optional\) **Customer provided**: When you select customer provided, you can specify exactly what test data you want to use\. If you select Customer provided test dataset, enter the URL of the annotations file in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the annotation files are located and choose **Select folder**\.

1. \(Optional\) If you want Amazon Comprehend to create a confusion matrix that provides metrics on how well the classifier performed during training, enter the location of an Amazon S3 bucket where it will be saved\. For more information, see [Confusion matrix](cer-doc-class.md#conf-matrix)\.

   \(Optional\) If you choose to encrypt the output result from your training job, choose **Encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key alias for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.

1. Choose **Choose an existing IAM role**, and then choose an existing IAM role that has read permissions for the S3 bucket that contains your training documents\. Only roles that have a trust policy that begins with comprehend\.amazonaws\.com are valid\.

   If you don't already have an IAM role with these permissions, choose **Create an IAM role** to make one\. Choose the access permissions to grant this role, and then choose a name suffix to distinguish the role from IAM roles in your account\.
**Note**  
If the input documents are encrypted, the IAM role used must also have `kms:Decrypt` permission\. For more information, see [Permissions required to use KMS encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnets\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your classification job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. \(Optional\) To add a tag to the custom classifier, enter a key\-value pair under **Tags**\. Choose **Add tag**\. To remove this pair before creating the classifier, choose **Remove tag**\. For more information, see [Tagging your resources](tagging.md)\.

1. Choose **Create**\.

The new classifier will then appear in the list, showing its status\. It will first show as `Submitted`\. It will then show `Training` for a classifier that is processing training documents, `Trained` for a classifier that is ready to use, and `In error` for a classifier that has an error\. You can click on a job to get more information about the classifier, including any error messages\.

![\[The custom classifier list.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/class-list.png)