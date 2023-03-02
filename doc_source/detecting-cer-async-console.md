# Starting a custom entity detection job \(console\)<a name="detecting-cer-async-console"></a>

You can use the console to start and monitor an async analysis job for custom entity recognition\.

**To start an async analysis job**

1. Sign in to the AWS Management Console and open the Amazon Comprehend console at [https://console\.aws\.amazon\.com/comprehend/](https://console.aws.amazon.com/comprehend/)

1. From the left menu, choose **Analysis jobs** and then choose **Create job**\.

1. Give the classification job a name\. The name must be unique your account and current Region\.

1. Under **Analysis type**, choose **Custom entity recognition**\.

1. From **Recognizer model**, choose the custom entity recognizer to use\.

1. From **Version**, choose the recognizer version to use\.

1. \(Optional\) If you choose to encrypt the data that Amazon Comprehend uses while processing your job, choose **Job encryption**\. Then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key ID under **KMS key ARN**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key management service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Input data**, enter the location of the Amazon S3 bucket that contains your input documents or navigate to it by choosing **Browse S3**\. This bucket must be in the same Region as the API that you are calling\. The IAM role that you're using for access permissions for the analysis job must have reading permissions for the S3 bucket\.

1. \(Optional\) for **Input format**, you can choose the format of the input documents\. The format can be one document per file, or one document per line in a single file\. One document per line applies only to text documents\. 

1. \(Optional\) For **Document read mode**, you can override the default text extraction actions\. For more information, see [Setting text extraction options](idp-set-textract-options.md)\. 

1. Under **Output data**, enter the location of the Amazon S3 bucket where Amazon Comprehend should write the job's output data or navigate to it by choosing **Browse S3**\. This bucket must be in the same Region as the API that you are calling\. The IAM role you're using for access permissions for the classification job must have write permissions for the S3 bucket\.

1. \(Optional\) if you choose to encrypt the output result from your job, choose **Encryption**\. Then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key alias or ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your analysis job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC that accesses the output bucket\.

1. Choose **Create job** to create the entity recognition job\.