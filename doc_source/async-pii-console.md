# PII asynchronous analysis jobs \(Console\)<a name="async-pii-console"></a>

You can use the console to create async analysis jobs to detect PII entities\. For more information about PII entity types, see [Detecting PII entities](how-pii.md)\.

**To create an analysis job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Analysis jobs** and then choose **Create job**\. 

1. Under **Job settings**, give the analysis job a unique name\.

1. For **Analysis type**, choose **Personally identifiable information \(PII\)**\.

1. From **Output mode**, select one of the following choices:
   + **Offsets** – The job output returns the location of each PII entity\. 
   + **Redactions** – The job output returns a copy of the input text with each PII entry redacted\.

1. \(Optional\)If you choose **Redactions** as the output mode, you can select the PII entity types to redact\.

1. Under **Input data**, specify where the input documents are located in Amazon S3:
   + To analyze your own documents, choose **My documents**, and choose **Browse S3** to provide the path to the bucket or folder that contains your files\.
   + To analyze samples that are provided by Amazon Comprehend, choose **Example documents**\. In this case, Amazon Comprehend uses a bucket that is managed by AWS, and you don't specify the location\.

1. \(Optional\) For **Input format**, specify one of the following formats for your input files:
   + **One document per file** – Each file contains one input document\. This is best for collections of large documents\.
   + **One document per line** – The input is one or more files\. Each line in a file is considered a document\. This is best for short documents, such as social media postings\. Each line must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. You can't use the UTF\-8 line separator \(u\+2028\) to end a line\.

1. Under **Output data**, choose **Browse S3**\. Choose the Amazon S3 bucket or folder where you want Amazon Comprehend to write the output data that is produced by the analysis\.

1. \(Optional\) To encrypt the output result from your job, choose **Encryption**\. Then, choose whether to use a KMS key associated with the current account or one from another account:
   + If you are using a key associated with the current account, choose the key alias or ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key management service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Access permissions**, provide an IAM role that:
   + Grants read access to the Amazon S3 location of your input documents\.
   + Grants write access to the Amazon S3 location of your output documents\.
   + Includes a trust policy that allows the `comprehend.amazonaws.com` service principal to assume the role and gain its permissions\.

   If you don't already have an IAM role with these permissions and an appropriate trust policy, choose **Create an IAM** role to create one\.

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.

The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. You can click on a job to get more information about the job, including any error messages\.

When the job is completed, Amazon Comprehend stores the analysis results in the output Amazon S3 location that you specified for the job\. For a description of the analysis results, see [Detecting PII entities](how-pii.md)\. 