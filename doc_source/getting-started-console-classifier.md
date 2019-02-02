# Creating a Document Classifier Using the Console<a name="getting-started-console-classifier"></a>

Create a document classifier to identify the categories of a set of documents\.

To train the classifier, you need a set of training documents\. You label these documents with the categories that you want the document classifier to recognize\. For more information, see [Custom Classification](how-document-classification.md)\.

**To train a document classifier**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Classification** and then choose **Create**\.

1. Give the classifier a name\. Then name must be unique within the region and account\.

1. Select the language of the training documents\. You can train a document classifier using any of the languages that work with Amazon Comprehend: English, Spanish, German, Italian, French, or Portuguese\. However, you can only train the classifier in one language\.

1. Choose the source of the data that you would like to use\. You can use either sample data or choose your own data stored in an S3 bucket\.

1. If you choose to use your own data, the total size of the training documents must be less than 5 Gb and you can provide up to 250 classification labels\. Provide the following information in the **Choose input data** section:
   + **S3 data location**—The Amazon S3 bucket that contains the training documents\. You can choose the **Search** button to browse to the location of your data\. The bucket must be in the same region as the API that you are calling\.
   + **Input format**—Only the format of one document per line in a file is supported\.
   + **Input labels S3 location**—The S3 location of the training documents\.

1. In the **Choose an IAM role** section, either select an existing IAM role or create a new one\.
   + **Choose an existing IAM role** – Choose this option if you already have an IAM role with permissions to access the input and output Amazon S3 buckets\.
   + **Create a new IAM role** – Choose this option when you want to create a new IAM role with the proper permissions for Amazon Comprehend to access the input and output buckets\. For more information about the permissions given to the IAM role, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

1. When you have finished filling out the form, choose **Create classifier** to create the document classifier\.

The new classifier appears in the list with the status field showing the status\. The field can be `TRAINING` for a classifier that is processing training documents, `TRAINED` for a document classifier that is ready to use, and `IN_ERROR` for a document classifier that has an error\. You can click on a job to get more information about the classifier, including any error messages\.

![\[The detail page for a document classifier.\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-image-60.png)