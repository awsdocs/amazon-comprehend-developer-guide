# Step 1: Adding Documents to Amazon S3<a name="tutorial-reviews-add-docs"></a>

Before starting the Amazon Comprehend analysis jobs, you need to store a sample dataset of customer reviews in Amazon Simple Storage Service \(Amazon S3\)\. Amazon S3 hosts your data in containers called buckets\. Amazon Comprehend can analyze documents stored in a bucket and it sends results of the analysis to a bucket\. In this step, you create an S3 bucket, create input and output folders in the bucket, and upload a sample dataset to the bucket\.

**Topics**
+ [Prerequisites](#tutorial-reviews-add-docs-prereqs)
+ [Download Sample Data](#tutorial-reviews-add-docs-download)
+ [Create an Amazon S3 Bucket](#tutorial-reviews-add-docs-bucket)
+ [\(Console Only\) Create Folders](#tutorial-reviews-add-docs-folders)
+ [Upload the Input Data](#tutorial-reviews-add-docs-upload)

## Prerequisites<a name="tutorial-reviews-add-docs-prereqs"></a>

Before you begin, review [Tutorial: Analyzing Insights from Customer Reviews with Amazon Comprehend](tutorial-reviews.md) and complete the prerequisites\.

## Download Sample Data<a name="tutorial-reviews-add-docs-download"></a>

The following sample dataset contains Amazon reviews taken from the larger dataset "Amazon reviews \- Full", which was published with the article "Character\-level Convolutional Networks for Text Classification" \(Xiang Zhang et al\., 2015\)\. Download the dataset to your computer\.

**To get the sample data**

1. Download the zip file [tutorial\-reviews\-data\.zip](samples/tutorial-reviews-data.zip) to your computer\.

1. Extract the zip file on your computer\. There are two files\. The file `THIRD_PARTY_LICENSES.txt` is the open source license for the dataset published by Xiang Zhang et al\. The file `amazon-reviews.csv` is the dataset you analyze in the tutorial\.

## Create an Amazon S3 Bucket<a name="tutorial-reviews-add-docs-bucket"></a>

After downloading the sample dataset, create an Amazon S3 bucket to store your input and output data\. You can create an S3 bucket using the Amazon S3 console or the AWS Command Line Interface \(AWS CLI\)\. 

### Create an Amazon S3 Bucket \(Console\)<a name="tutorial-reviews-add-docs-bucket-console"></a>

In the Amazon S3 console, you create a bucket with a name that is unique in all of AWS\.

**To create an S3 bucket \(console\)**

1. Sign in to the AWS Management Console and open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In **Buckets**, choose **Create bucket**\.

1. For **Bucket name**, enter a globally unique name that describes the bucket's purpose\.

1. For **Region**, choose the AWS Region where you want to create the bucket\. The Region you choose must support Amazon Comprehend\. To reduce latency, choose the AWS Region closest to your geographic location that is supported by Amazon Comprehend\. For a list of Regions that support Amazon Comprehend, see the [Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) in the *Global Infrastructure Guide*\.

1. Leave the default settings for **Object Ownership**, **Bucket settings for Block Public Access**, **Bucket Versioning**, and **Tags**\.

1. For **Default encryption**, choose **Disable**\. 
**Tip**  
While this tutorial does not use encryption, you might want to use encryption when analyzing important data\. For end\-to\-end encryption, you can encrypt your data at rest in the bucket and also when you run analysis jobs\. For more information about encryption with AWS, see [What is AWS Key Management Service?](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html) in the *AWS Key Management Service Developer Guide*\.

1. Review your bucket configurations and then choose **Create bucket**\.

### Create an Amazon S3 Bucket \(AWS CLI\)<a name="tutorial-reviews-add-docs-bucket-cli"></a>

After opening the AWS CLI, you run the `create-bucket` command to create a bucket that will store the input and output data\.

**To create an Amazon S3 bucket \(AWS CLI\)**

1. To create your bucket, run the following command in the AWS CLI\. Replace *DOC\-EXAMPLE\-BUCKET* with a name for the bucket that is unique in all of AWS\.

   ```
   aws s3api create-bucket --bucket DOC-EXAMPLE-BUCKET
   ```

   By default, the `create-bucket` command creates a bucket in the `us-east-1` AWS Region\. To create a bucket in an AWS Region other than `us-east-1`, add the `LocationConstraint` parameter to specify your Region\. For example, the following command creates a bucket in the `us-west-2` Region\.

   ```
   aws s3api create-bucket --bucket DOC-EXAMPLE-BUCKET
   --region us-west-2 --create-bucket-configuration LocationConstraint=us-west-2
   ```

   Note that only certain Regions support Amazon Comprehend\. For a list of Regions that support Amazon Comprehend, see the [Region Table](http://aws.amazon.com/about-aws/global-infrastructure/regional-product-services/) in the *Global Infrastructure Guide*\.

1. To ensure that your bucket was created successfully, run the following command\. The command lists all of the S3 buckets associated with your account\.

   ```
   aws s3 ls
   ```

## \(Console Only\) Create Folders<a name="tutorial-reviews-add-docs-folders"></a>

Next, create two folders in your S3 bucket\. The first folder is for your input data\. The second folder is where Amazon Comprehend sends the analysis results\. If you use the Amazon S3 console, you have to manually create the folders\. If you use the AWS CLI, you can create folders when you upload the sample dataset or run an analysis job\. For that reason, we provide a procedure for creating folders only for console users\. If you are using the AWS CLI, you will create folders in [Upload the Input Data](#tutorial-reviews-add-docs-upload) and in [Step 3: Running Analysis Jobs on Documents in Amazon S3](tutorial-reviews-analysis.md)\.

**To create folders in your S3 bucket \(console\)**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In **Buckets**, choose your bucket from the list of buckets\.

1. In the **Overview** tab, choose **Create folder**\.

1. For the new folder name, enter `input`\.

1. For the encryption settings, choose **None \(Use bucket settings\)**\.

1. Choose **Save**\.

1. Repeat steps 3 through 6 to create another folder for the output of the analysis jobs, but in step 4, enter the new folder name `output`\.

## Upload the Input Data<a name="tutorial-reviews-add-docs-upload"></a>

Now that you have a bucket, upload the sample dataset `amazon-reviews.csv`\. You can upload data to S3 buckets with the Amazon S3 console or the AWS CLI\. 

### Upload Sample Documents to a Bucket \(Console\)<a name="tutorial-reviews-add-docs-upload-console"></a>

In the Amazon S3 console, upload the sample dataset file to the input folder\.

**To upload the sample documents \(console\)**

1. Open the Amazon S3 console at [https://console\.aws\.amazon\.com/s3/](https://console.aws.amazon.com/s3/)\.

1. In **Buckets**, choose your bucket from the list of buckets\.

1. Choose the `input` folder and then choose **Upload**\.

1. Choose **Add files** and then choose the `amazon-reviews.csv` file on your computer\.

1. Choose **Next**\.

1. Leave the default settings for **Manage users**, **Access for other AWS accounts**, and **Manage public permissions**\. Choose **Next**\.

1. For **Storage class**, choose **Standard**\.

1. For **Encryption**, choose **None**\.

1. Leave **Metadata** and **Tag** blank\.

1. Choose **Next** and review the configurations, and then choose **Upload**\.

### Upload Sample Documents to a Bucket \(AWS CLI\)<a name="tutorial-reviews-add-docs-upload-cli"></a>

Create an input folder in your S3 bucket and upload the dataset file to the new folder with the `cp` command\.

**To upload the sample documents \(AWS CLI\)**

1. To upload the `amazon-reviews.csv` file to a new folder in your bucket, run the following AWS CLI command\. Replace *DOC\-EXAMPLE\-BUCKET* with the name of your bucket\. By adding the path `/input/` at the end, Amazon S3 automatically creates a new folder called `input` in your bucket and uploads the dataset file to that folder\.

   ```
   aws s3 cp amazon-reviews.csv s3://DOC-EXAMPLE-BUCKET/input/
   ```

1. To ensure that your file was uploaded successfully, run the following command\. The command lists the contents of your bucket's `input` folder\.

   ```
   aws s3 ls s3://DOC-EXAMPLE-BUCKET/input/
   ```

Now, you have an S3 bucket with the `amazon-reviews.csv` file in a folder called `input`\. If you used the console, you also have an `output` folder in the bucket\. If you used the AWS CLI, you will create the output folder when running the Amazon Comprehend analysis jobs\.