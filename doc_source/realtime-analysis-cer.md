# Train custom recognizers \(console\)<a name="realtime-analysis-cer"></a>

You can create custom entity recognizers using the Amazon Comprehend console\. This section shows you how to create and train a custom entity recognizer\.

**Topics**

## Creating a custom entity recognizer using the console \- CSV format<a name="console-CER"></a>

To create the custom entity recognizer, first provide a dataset to train your model\. With this dataset, include one of the following: a set of annotated documents or a list of entities and their type label, along with a set of documents containing those entities\. For more information, see [Custom entity recognition](custom-entity-recognition.md)

**To train a custom entity recognizer with a CSV file**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Customization** and then choose **Custom entity recognition**\.

1. Choose **Create new model**\.

1. Give the recognizer a name\. The name must be unique within the Region and account\.

1. Select the language\. 

1. Under **Custom entity type**, enter a custom label that you want the recognizer to find in the dataset\. 

   The entity type must be uppercase, and if it consists of more than one word, separate the words with an underscore\. 

1. Choose **Add type**\.

1. If you want to add an additional entity type, enter it, and then choose **Add type**\. If you want to remove one of the entity types you've added, choose **Remove type** and then choose the entity type to remove from the list\. A maximum of 25 entity types can be listed\. 

1. To encrypt your training job, choose **Recognizer encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, for **KMS key ID** choose the key ID\.
   + If you are using a key associated with a different account, for **KMS key ARN** enter the ARN for the key ID\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Data specifications**, choose the format of your training documents:
   + **CSV file** — A CSV file that supplements your training documents\. The CSV file contains information about the custom entities that your trained model will detect\. The required format of the file depends on whether you are providing annotations or an entity list\.
   + **Augmented manifest** — A labeled dataset that is produced by Amazon SageMaker Ground Truth\. This file is in JSON lines format\. Each line is a complete JSON object that contains a training document and its labels\. Each label annotates a named entity in the training document\. You can provide up to 5 augmented manifest files\.

   For more information about available formats, and for examples, see [Training custom entity recognizer models](training-recognizers.md)\.

1. Under **Training type**, choose the training type to use:
   + **Using annotations and training docs**
   + **Using entity list and training docs**

    If choosing annotations, enter the URL of the annotations file in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the annotation files are located and choose **Browse S3**\.

    If choosing entity list, enter the URL of the entity list in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the entity list is located and choose **Browse S3**\.

1. Enter the URL of an input dataset containing the training documents in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the training documents are located and choose **Select folder**\.

1. Under **Test dataset** select how you want to evaluate the performance of your trained model \- you can do this for both annotations and entity list training types\.
   + **Autosplit**: Autosplit automatically selects 10% of your provided training data to use as testing data 
   + \(Optional\) **Customer provided**: When you select customer provided, you can specify exactly what test data you want to use\.

1. If you select Customer provided test dataset, enter the URL of the annotations file in Amazon S3\. You can also navigate to the bucket or folder in Amazon S3 where the annotation files are located and choose **Select folder**\.

1. In the **Choose an IAM role** section, either select an existing IAM role or create a new one\.
   + **Choose an existing IAM role** – Select this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.
   + **Create a new IAM role** – Select this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. 
**Note**  
If the input documents are encrypted, the IAM role used must have `kms:Decrypt` permission\. For more information, see [Permissions required to use KMS encryption](security_iam_id-based-policy-examples.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your custom entity recognition job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. \(Optional\) To add a tag to the custom entity recognizer, enter a key\-value pair under **Tags**\. Choose **Add tag**\. To remove this pair before creating the recognizer, choose **Remove tag**\.

1. Choose **Train**\.

The new recognizer will then appear in the list, showing its status\. It will first show as `Submitted`\. It will then show `Training` for a classifier that is processing training documents, `Trained` for a classifier that is ready to use, and `In error` for a classifier that has an error\. You can click on a job to get more information about the recognizer, including any error messages\.

## Creating a custom entity recognizer using the console \- augmented manifest<a name="getting-started-CER-PDF"></a>

**To train a custom entity recognizer with a plaintext, PDF, or word document**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Customization** and then choose **Custom entity recognition**\.

1. Choose **Train recognizer**\.

1. Give the recognizer a name\. The name must be unique within the Region and account\.

1. Select the language\. Note: If you're training a PDF or Word document, English is the supported language\. 

1. Under **Custom entity type**, enter a custom label that you want the recognizer to find in the dataset\. 

   The entity type must be uppercase, and if it consists of more than one word, separate the words with an underscore\.

1. Choose **Add type**\.

1. If you want to add an additional entity type, enter it, and then choose **Add type**\. If you want to remove one of the entity types you've added, choose **Remove type** and then choose the entity type to remove from the list\. A maximum of 25 entity types can be listed\. 

1. To encrypt your training job, choose **Recognizer encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, for **KMS key ID** choose the key ID\.
   + If you are using a key associated with a different account, for **KMS key ARN** enter the ARN for the key ID\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [AWS Key Management Service](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Training data**, choose **Augmented manifest** as your data format:
   + **Augmented manifest** — is a labeled dataset that is produced by Amazon SageMaker Ground Truth\. This file is in JSON lines format\. Each line in the file is a complete JSON object that contains a training document and its labels\. Each label annotates a named entity in the training document\. You can provide up to 5 augmented manifest files\. If you are using PDF documents for training data, you must select **Augmented manifest**\. You can provide up to 5 augmented manifest files\. For each file, you can name up to 5 attributes to use as training data\.

   For more information about available formats, and for examples, see [Training custom entity recognizer models](training-recognizers.md)\.

1. Select the training model type\. 

   If you selected **Plaintext documents**, under **Input location**, enter the Amazon S3URL of the Amazon SageMakerGround Truth augmented manifest file\. You can also navigate to the bucket or folder in Amazon S3 where the augmented manifest\(s\) is located and choose **Select folder**\.

1. Under **Attribute name**, enter the name of the attribute that contains your annotations\. If the file contains annotations from multiple chained labeling jobs, add an attribute for each job\. In this case, each attribute contains the set of annotations from a labeling job\. Note: You can provide up to 5 attribute names for each file\.

1. Select **Add**\.

1. If you selected **PDF, Word documents** under **Input location**, enter the Amazon S3URL of the Amazon SageMaker Ground Truth augmented manifest file\. You can also navigate to the bucket or folder in Amazon S3 where the augmented manifest\(s\) is located and choose **Select folder**\.

1. Enter the S3 prefix for your **Annotation** data files\. These are the PDF documents that you labled\.

1. Enter the S3 prefix for your **Source** documents\. These are the original PDF documents \(data objects\) that you provided to Ground Truth for your labeling job\.

   

1. Enter the attribute names that contain your annotations\. Note: You can provide up to 5 attribute names for each file\. Any attributes in your file that you don't specify are ignored\. 

1. In the IAM role section, either select an existing IAM role or create a new one\.
   + **Choose an existing IAM role** – Select this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.
   + **Create a new IAM role** – Select this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. 
**Note**  
If the input documents are encrypted, the IAM role used must have `kms:Decrypt` permission\. For more information, see [Permissions required to use KMS encryption](security_iam_id-based-policy-examples.md#auth-kms-permissions)\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your custom entity recognition job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the input documents and the output bucket are accessed\.

1. \(Optional\) To add a tag to the custom entity recognizer, enter a key\-value pair under **Tags**\. Choose **Add tag**\. To remove this pair before creating the recognizer, choose **Remove tag**\.

1. Choose **Train**\.

The new recognizer will then appear in the list, showing its status\. It will first show as `Submitted`\. It will then show `Training` for a classifier that is processing training documents, `Trained` for a classifier that is ready to use, and `In error` for a classifier that has an error\. You can click on a job to get more information about the recognizer, including any error messages\.