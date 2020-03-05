# Creating a Custom Entity Recognizer Using the Console<a name="getting-started-console-CER"></a>

To create the custom entity recognizer, first provide a dataset to train your model\. With this dataset, include one of the following\. A set of annotated documents or a list of entities and their type label, along with a set of documents containing those entities\. For more information, see [Custom Entity Recognition](custom-entity-recognition.md)

**To train a custom entity recognizer**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom entity recognizer**\.

1. Choose **Train recognizer**\.

1. Give the recognizer a name\. The name must be unique within the Region and account\.

1. Under **Custom entity type**, enter a custom label that you want the recognizer to find in the dataset\. 

   The entity type must be uppercase, and if it consists of more than one word, separate the words with an underscore\.

1. Choose **Add type**\.

1. If you want to add an additional entity type, enter it, and then choose **Add type**\. If you want to remove one of the entity types you've added, choose **Remove type** and then choose the entity type to remove from the list\. A maximum of 12 entity types can be listed\. 

1. To encrypt your training job, choose **Recognizer encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, for **KMS key ID** choose the key ID\.
   + If you are using a key associated with a different account, for **KMS key ARN** enter the ARN for the key ID\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key Management Service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Training data**, choose the training type to use:
   + **Using annotations and training docs**
   + **Using entity list and training docs**

    If choosing annotations, enter the URL of the annotations file in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the annotation files are located and choose **Select folder**\. The file or files must be in \.csv format\. 

    If choosing entity list, enter the URL of the entity list in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the entity list is located and choose **Select folder**\. The file must be in \.csv format\. 

1. Enter the URL of an input dataset containing the training documents in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the training documents are located and choose **Select folder**\. The file must be in \.csv format\. 

1. In the **Choose an IAM role** section, either select an existing IAM role or create a new one\.
   + **Choose an existing IAM role** – Select this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.
   + **Create a new IAM role** – Select this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. 
**Note**  
If the input documents are encrypted, the IAM role used must have `kms:Decrypt` permission\. For more information, see [Permissions Required to Use KMS Encryption](access-control-managing-permissions.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your custom entity recognition job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. \(Optional\) To add a tag to the custom entity recognizer, enter a key\-value pair under **Tags**\. Choose **Add tag**\. To remove this pair before creating the recognizer, choose **Remove tag**\.

1. Choose **Train**\.

The new recognizer will then appear in the list, showing its status\. It will first show as `Submitted`\. It will then show `Training` for a classifier that is processing training documents, `Trained` for a classifier that is ready to use, and `In error` for a classifier that has an error\. You can click on a job to get more information about the recognizer, including any error messages\.