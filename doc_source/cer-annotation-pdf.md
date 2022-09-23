# Annotating PDF files<a name="cer-annotation-pdf"></a>

Before you can annotate your training PDFs in SageMaker Ground Truth, you'll need to complete a few prerequisites:
+ Install python3\.8\.x
+ Install the AWS CLI

  If you're using the us\-east\-1 Region, you can skip installing the AWS CLI because it's already installed with your Python environment\. In this case, you'll create a virtual environment to use Python 3\.8 in AWS Cloud9\.
+ Install [jq](https://stedolan.github.io/jq/download/)
+ Configure your [AWS credentials](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)
+ Create a private [SageMaker Ground Truth workforce](https://docs.aws.amazon.com/sagemaker/latest/dg/sms-workforce-private-use-cognito.html) to support annotation

  Make sure to record the workteam name you choose in your new private workforce, as you'll be required to use it during installation\.

**Topics**
+ [Setting up your environment](#cer-annotation-pdf-set-up)
+ [Uploading a PDF to an S3 bucket](#cer-annotation-pdf-upload)
+ [Creating an annotation job](#cer-annotation-pdf-job)
+ [Annotating with SageMaker Ground Truth](#w360aac31c23c19c19c15)

## Setting up your environment<a name="cer-annotation-pdf-set-up"></a>

1. If using Windows, install [Cygwin](https://cygwin.com/install.html); if using Linux or Mac, skip this step\.

1. Download the [annotation artifacts](http://github.com/aws-samples/amazon-comprehend-semi-structured-documents-annotation-tools) from GitHub\. Unzip the file\.

1. From your terminal window, navigate to the unzipped folder \(**amazon\-comprehend\-semi\-structured\-documents\-annotation\-tools\-main**\)\. This folder includes a `Makefile` that you run to install dependencies, setup a Python virtualenv, and deploy the required resources\.

1. Run the following command to install the AWS CLI, [Pipenv](https://pypi.org/project/pipenv/), [AWS SAM](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/what-is-sam.html), other dependencies, and set up a virtual environment:

   `make bootstrap`

1. The following command runs basic python checkstyle and cnf\-lint, and builds the AWS CloudFormation template using the AWS SAM CLI: 

   `make build`

1. <a name="deploy-guided"></a>To create and deploy the CloudFormation stack, run the following command\. It packages the AWS CloudFormation template to be ready for deployment, and launches the AWS SAM deployment command with interactive guidance:

   `make deploy-guided`

   This command presents a set of configuration options\. Be sure your AWS Region is correct\. For all other fields, you can either accept the default values or fill in custom values\. If you modify the AWS CloudFormation stack name, write it down as you need it in the next steps\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/deploy_guided_anno.png)

   The command defines a CloudFormation stack\. This CloudFormation stack will create and manage the [AWS lambdas](https://aws.amazon.com/lambda/), [AWS IAM](https://aws.amazon.com/iam/) roles, and [AWS S3](https://aws.amazon.com/s3/) buckets required for the annotation tool\.

   You can review each of these resources in the stack details page in the CloudFormation console\.

1. The command prompts you to start the deployment\. CloudFormation creates all the resources in the specified Region\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/deploy_guided_anno_2.png)

   When the CloudFormation stack status transitions to create\-complete, the resources are ready to use\.

## Uploading a PDF to an S3 bucket<a name="cer-annotation-pdf-upload"></a>

In step [Step 6](#deploy-guided), you deployed a CloudFormation stack that creates an S3 bucket named **comprehend\-semi\-structured\-documents\-$\{AWS::Region\}\-$\{AWS::AccountId\}**\. You now upload your source PDF documents into this bucket\.

**Note**  
This bucket contains the data required for your labeling job\. The Lambda Execution Role policy grants permission for the Lambda function to access this bucket\.  
You can find the S3 bucket name in the **CloudFormation Stack details** using the '**SemiStructuredDocumentsS3Bucket**' key\.

1. Create a new folder in the S3 bucket\. Name this new folder '**src**'\. 

1. Add your PDF source files to your '**src**' folder\. In a later step, you annotate these files to train your recognizer\.

1. \(Optional\) Here's an AWS CLI example you can use to upload your source documents from a local directory into an S3 bucket:

   `aws s3 cp --recursive local-path-to-your-source-docs s3://deploy-guided/src/`

   Or, with your Region and Account ID:

   `aws s3 cp --recursive local-path-to-your-source-docs s3://deploy-guided-Region-AccountID/src/`

1. You now have a private SageMaker Ground Truth workforce and have uploaded your source files to the S3 bucket, **deploy\-guided/src/**; you're ready to start annotating\.

## Creating an annotation job<a name="cer-annotation-pdf-job"></a>

The **comprehend\-ssie\-annotation\-tool\-cli\.py** script in the `bin` directory is a simple wrapper command that streamlines the creation of a SageMaker Ground Truth labeling job\. The python script reads the source documents from your S3 bucket and creates a corresponding single\-page manifest file with one source document per line\. The script then creates a labeling job, which requires the manifest file as an input\. 

The python script uses the S3 bucket and CloudFormation stack that you configured in [Step 6](#deploy-guided)\. Required input parameters for the script include:
+ **input\-s3\-path**: S3 Uri to the source documents you uploaded to your S3 bucket\. For example: `s3://deploy-guided/src/`\. You can also add your Region and Account ID to this path\. For example: `s3://deploy-guided-Region-AccountID/src/`\.
+ **cfn\-name**: The CloudFormation stack name\. If you used the default value in [Step 6](#deploy-guided), your cfn\-name is **sam\-app**\.
+ **work\-team\-name**: The workforce name you created when you built out the private workforce in SageMaker Ground Truth\.
+ **job\-name\-prefix**: The prefix for the SageMaker Ground Truth labeling job\. Note that there is a 29\-character limit for this field\. A timestamp is appended to this value\. For example: `my-job-name-20210902T232116`\.
+ **entity\-types**: The entities you want to use during your labeling job, separated by commas\. This list must include all entities that you want to annotate in your training dataset\. The Ground Truth labeling job displays only these entities for annotators to label content in the PDF documents\. 

To view additional arguments the script supports, use the `-h` option to display the help content\.
+ Run the following script with the input parameters as described in the previous list\.

  ```
  python bin/comprehend-ssie-annotation-tool-cli.py \
  --input-s3-path s3://deploy-guided-Region-AccountID/src/ \
  --cfn-name sam-app \
  --work-team-name my-work-team-name \
  --region us-east-1 \
  --job-name-prefix my-job-name-20210902T232116 \
  --entity-types "EntityA, EntityB, EntityC" \
  --annotator-metadata "key=info,value=sample,key=Due Date,value=12/12/2021"
  ```

  The script produces the following output:

  ```
  Downloaded files to temp local directory /tmp/a1dc0c47-0f8c-42eb-9033-74a988ccc5aa
  Deleted downloaded temp files from /tmp/a1dc0c47-0f8c-42eb-9033-74a988ccc5aa
  Uploaded input manifest file to s3://comprehend-semi-structured-documents-us-west-2-123456789012/input-manifest/my-job-name-20220203-labeling-job-20220203T183118.manifest
  Uploaded schema file to s3://comprehend-semi-structured-documents-us-west-2-123456789012/comprehend-semi-structured-docs-ui-template/my-job-name-20220203-labeling-job-20220203T183118/ui-template/schema.json
  Uploaded template UI to s3://comprehend-semi-structured-documents-us-west-2-123456789012/comprehend-semi-structured-docs-ui-template/my-job-name-20220203-labeling-job-20220203T183118/ui-template/template-2021-04-15.liquid
  Sagemaker GroundTruth Labeling Job submitted: arn:aws:sagemaker:us-west-2:123456789012:labeling-job/my-job-name-20220203-labeling-job-20220203t183118
  (amazon-comprehend-semi-structured-documents-annotation-tools-main) user@3c063014d632 amazon-comprehend-semi-structured-documents-annotation-tools-main %
  ```

## Annotating with SageMaker Ground Truth<a name="w360aac31c23c19c19c15"></a>

Now that you have configured the required resources and created a labeling job, you can log in to the labeling portal and annotate your PDFs\.

1. Log in to the [SageMaker console](https://console.aws.amazon.com/sagemaker) using either Chrome or Firefox web browsers\.

1. Select **Labeling workforces** and choose **Private**\.

1. Under **Private workforce summary**, select the labeling portal sign\-in URL that you created with your private workforce\. Sign in with the appropriate username and password\.

   If you don't see any jobs listed, don't worry—it can take a while to update, depending on the number of files you uploaded for annotation\.

1. Select your task and, in the top right corner, choose **Start working** to open the annotation screen\.

   You'll see one of your documents open in the annotation screen and, above it, the entity types you provided during set up\. To the right of your entity types, there is an arrow you can use to navigate through your documents\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/annotation_demo1.png)

   Annotate the open document\. You can also remove, undo, or auto tag your annotations on each document; these options are available in the right panel of the annotation tool\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/data_annotation.png)

   To use auto tag, annotate an instance of one of your entities; all other instances of that specific word are then automatically annotated with that entity type\.

   Once you've finished, select **Submit** on the bottom right, then use the navigation arrows to move to the next document\. Repeat this until you've annotated all your PDFs\.

After you annotate all the training documents, you can find the annotations in JSON format in the Amazon S3 bucket at this location:

```
/output/your labeling job name/annotations/
```

The output folder also contains an output manifest file, which lists all the annotations within your training documents\. You can find your output manifest file at the following location\.

```
/output/your labeling job name/manifests/
```