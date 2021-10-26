# PDF Annotations<a name="pdf-word-annotation"></a>

With Amazon Comprehend you can train your models and use your models to gain insight on text files, PDFs, and Word documents\. Before you can annotate your training PDFs in SageMaker Ground Truth, there are a few prerequisites and tools required\. The lifecycle of this process consists of three main parts \- installing the prerequisites and *preparing* your environments, *building* out the tool, and then once everything is set up, *annotating*\. During this process you'll be required to go to a few places —you'll be pulling our resources from [GitHub](github.com/aws-samples/amazon-comprehend-semi-structured-documents-annotation-tools), you'll be working locally on your machine, you'll run commands in the AWS CLI, and you'll end up in the AWS Console and in SageMaker Ground Truth\. This process might take 20 \- 25 minutes\. If you have any questions or need assistence, please reach out to [AWS support](https://aws.amazon.com/contact-us/)\. 

## Prerequisites<a name="w57aac23c11c15c49b5"></a>
+ Install python3\.8\.x \(e\.g\. You can use [pyenv](https://github.com/pyenv/pyenv) for python version management\) 
+ Install [jq ](https://stedolan.github.io/jq/download/)
+ Have AWS credentials configured \- you can do this from the [Configuration and credential file setting](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html) page 
+ Create a private SageMaker Ground Truth workforce to support annotation\. See instructions here \- [Create and Manage Private SageMaker Ground Truth Workforce](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-workforce-private-use-cognito.html)\. 
**Important**  
Make sure to record the corresponding workteam name you created in your new private workforce\. You'll be required to use it during installation\. 

If you are installing this tool in the us\-east\-1 Region you can skip installing the AWS CLI and AWS SAM CLI, because it’s already installed with your Python environment\. You just need to create a virtual environment to use Python 3\.8 in AWS Cloud9\.

## Get Resources from GitHub<a name="w57aac23c11c15c49b9"></a>

In this step, you navigate to Git Hub to get the resources required for you to build out the annotation tooling locally\. Download the annotation artifacts from **[github\.com/aws\-samples/amazon\-comprehend\-semi\-structured\-documents\-annotation\-tools](http://github.com/aws-samples/amazon-comprehend-semi-structured-documents-annotation-tools)**

## Run and Configure From the AWS CLI<a name="w57aac23c11c15c49c11"></a>

Once you've downloaded the \.zip file, unzip the annotation code\. Then, head to the AWS CLI and navigate into the **ComprehendSSIEAnnotationTool** folder\. 

**Note**  
The following instructions are for Linux/Ubuntu/Mac\. For Windows, please install [Cygwin](https://cygwin.com/install.html) and follow the same instructions\.

1. From the folder, run:

   `make bootsrap`

1. Run the command:

   `make build`

1. Next, run the following command to build out the CloudFormation template\. The template will be ready for your CloudFormation deployment\. This CloudFormation stack will manage the [AWS Lambdas](https://aws.amazon.com/lambda/) you created, [AWS IAM](https://aws.amazon.com/iam/) roles, and your [AWS S3](https://aws.amazon.com/s3/) bucket:

   `make deploy-guided`

   When you run the command, you are prompted to name the stack\. If you leave it blank, the default name is listed as **sam\-app**\.

1. You are presented with a set of configuration options\. You can accept all of them as default, except make sure you select your correct AWS Region\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/deploy_guided_anno.png)

1. Enter the values\. Your deployment successfully initiates\. This step linked your AWS account and resources to your AWS S3 bucket and your IAM roles\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/deploy_guided_anno_2.png)

## Upload PDF to Amazon S3 Bucket<a name="w57aac23c11c15c49c13"></a>

In step 3, you deployed a CloudFormation stack which contains an S3 bucket which is named **make\-deploy\-guided**\. This bucket is used to store all the data that is needed for your labeling job, and it is also referred to by the Lambda IAM Execution Role policy to ensure the Lambda functions have necessary permission to access the data\. The S3 bucket name can be found in **CloudFormation Stack Outputs **with a Key of **SemiStructuredDocumentsS3Bucket**\. You need to upload your source PDF documents into this Bucket\. 

1. In your S3 bucket, **make\-deploy\-guided**, create a new folder\.

1. Name your folder **/src**\.

1. Add your source files to the folder\. These are PDF files which you will annotate to train your recognizer\.

Here is a sample AWS CLI command you can use to directly upload source documents from your local directory to the S3 bucket: 
+ local\-path\-to\-source\-docs: the file path to local source documents
+ source\-folder\-name: name of a folder within the CloudFormation stack's managed S3 bucket

  `AWS_REGION= ` aws configure get region` ;`

  `AWS_ACCOUNT_ID= ` aws sts get-caller-identity | jq -r '.Account' `;`

  `aws s3 cp --recursive < local-path-to-source-docs> s3: // comprehend-semi-structured-documents- ${ AWS_REGION} -${ AWS_ACCOUNT_ID} / < source-folder-name> /`

## CLI \- Create Your Annotation Job<a name="w57aac23c11c15c49c15"></a>

At this point, you should have a private SageMaker Ground Truth workforce and you've built out and uploaded your source files to the S3 bucket\. Now it's time to finish up in the CLI\. After you've run **make deploy\-guided**, you are presented with some settings you need to update in your job creation script



1. **input\-s3\-path**: S3 Uri to the source documents you uploaded to your S3 bucket 

1. **cfn\-name**: The CloudFormation stack name
**Important**  
Write down the default CloudFormation name, you will need it in the next steps\. 

1.  **work\-team\-name**: The workforce name you created when you build out the private workforce in SageMaker Ground Truth

1. **job\-name\-prefix**: The prefix for the SageMaker Ground Truth labeling job \(LIMIT: 29 characters\)\. Extra text will be appended to job name prefix, ex\. \-labeling\-job\-task\-20210902T232116 

1. **entity\-types**: The entities you would like to use during the labeling job \(separated by commas\)\. This should be an exhaustive list of all the entities, across all document types in the training dataset\.

1. Copy and run the script with these updated details\.

     
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/annotation_settings.png)

The comprehend\-ssie\-annotation\-tool\-cli\.py under bin/ directory is a simple wrapper command that can be used streamline the creation of a SageMaker GroundTruth Job\. Under the hood, this CLI will read the source documents from the S3 path that you specify, and create a corresponding input manifest file with a single page of one source document per line, and the input manifest file is then used as input to your labeling job\.

## Annotating with SageMaker Ground Truth<a name="w57aac23c11c15c49c17"></a>

You are ready to start annotating your documents\.

1. Login to the AWS Console and navigate to Amazon SageMaker\.

1. Select **Labeling workforces** and choose **Private**\.

1. Under **Private workforce summary** you should see the labeling portal sign\-in URL which you created in a prerequisite step\. 

1. Select the sign\-in URL\.

1. Sign in with the username and password you selected when you created your private workforce\.

1. Select the sign\-in URL\. Once you're in, you might not see any jobs \- it can take some time to update depending on how many files you uploaded for annotation\.
**Note**  
Firefox and Chrome are the supported browsers\. 

1. Once your task populates, select the task and in the top right corner choose **Start working** to open to annotation screen\. 

   On the annotation screen you will see one of your documents open\. Above the document, you'll see the entity types you provided during set up\. To the right of your entity types you will see an arrow to navigate through your documents\. Once you have finished annotating your document and before you move on to the next one, make sure you select **Submit **on the bottom right\. 

   You also have options to **Remove**, **Undo**, or **Auto tag** your annotations on each document\. To use auto tag, simply annotate a word which is an instance of one of your entity types\. If you select Auto tag, all of the other instances of that entity type \(for example, instances of the same company name\) will be automatically annotated with that entity type \(CompanyName\)\. 

   

   Here is an example of an annotation screen\. You can see the entity types at the top above the PDF \- those will change depending on what entitiy types you listed during setup\. On the top right, you can move through the PDFs you have\. Remember \- after you annotate each PDF, select **Submit** on the bottom of the screen to save your annotations\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/annotation_demo1.png)

   In this image, you see the details from the right panel of the annotation tool\. You can edit, copy, remove and reset your annotations from this section\. To learn about PDF annotation best practices, please see [Annotation Best Practices](annotation-best-practices.md)  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/data_annotation.png)