# Creating an Events Detection Job Using the Console<a name="getting-started-console-events"></a>

You can use the Amazon Comprehend console to create and manage asynchronous events detection jobs\.

**To create an events detection job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Analysis jobs** and then choose **Create job**\. 

1. Under **Job settings**, give the analysis job a unique name\.

1. For **Analysis type**, choose **Events**\.

1. For **Language**, choose the language of your input documents\.

1. For **Target event types**, select the types of events to detect in your input documents\. For more information about supported event types, see [Event Types](how-events.md#events-types)\.

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
For more information on creating and using KMS keys and the associated encryption, see [Key Management Service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Access permissions**, provide an IAM role that:
   + Grants read access to the Amazon S3 location of your input documents\.
   + Grants write access to the Amazon S3 location of your output documents\.
   + Includes a trust policy that allows the `comprehend.amazonaws.com` service principal to assume the role and gain its permissions\.

   If you don't already have an IAM role with these permissions and an appropriate trust policy, choose **Create an IAM** role to create one\.

1. When you have finished filling out the form, choose **Create job** to create and start the topic detection job\.

The new job appears in the job list with the status field showing the status of the job\. The field can be `IN_PROGRESS` for a job that is processing, `COMPLETED` for a job that has finished successfully, and `FAILED` for a job that has an error\. You can click on a job to get more information about the job, including any error messages\.