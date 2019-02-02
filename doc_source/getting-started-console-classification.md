# Creating a Document Classification Job Using the Console<a name="getting-started-console-classification"></a>

Once you have created a document classifier, you can use it to categorize a group of documents\.

**To create a document classification job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Analysis** and then choose **Create**\.

1. In the **Configure** section, give the classification job a name\. The name must be unique in the region and account\.

1. From the **Analysis type** drop down, choose **Custom classification**\.

1. Form the **Select classifier** drop down select the document classifier to use\.

1. Choose the source of the data that you would like to use\. You can use either sample data or choose your own data stored in an S3 bucket\.

1. If you choose to use your own data, provide the following information in the **Choose input data** section:
   + **S3 data location**—An Amazon S3 bucket that contains the training documents\. You can choose the **Search** button to browse to the location of your data\. The bucket must be in the same region as the API that you are calling\.
   + **Input format**—Choose whether the training data is contained in one document per file, or if there is one document per line in a file\.
   + **Input labels S3 location**—If your training data is in one document per file, choose the S3 location of the label file\. You can choose the **Search** button to browse to the location of your data\.

1. Choose **Create** to create the document classification job\.