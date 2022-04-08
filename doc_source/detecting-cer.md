# Analysis jobs for custom entity recognition \(console\)<a name="detecting-cer"></a>

You can run an asynchronous analysis job to detect custom entities in a set of one or more documents\. The input files can include text files, image files, PDFs, or Word documents\. For files other than text files, Amazon Comprehend performs text extraction prior to the analysis\.

**Before you begin**  
You need a custom entity recognition model \(also known as a recognizer\) before you can detect custom entities\. A recognizer that is trained with plain\-text annotations supports entity detection for plain\-text documents only\. A recognizer that is trained with PDF document annotations supports entity detection for plain\-text documents, images, PDF files, and Word documents\.  
For more information about these models, see [Training recognizer models](training-recognizers.md)\. 

To start the job, you perform the following steps:

1. Store the documents in an Amazon S3 bucket\.

1. Invoke the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) API operation to start the asynchronous job\.

1. Monitor the progress of the analysis job\.

1. When the job is complete, retrieve the results of the analysis from the S3 bucket that you specified when you started the job\.

The custom entity recognition job searches for all the entities that the model was trained to find\. 

**Topics**
+ [Starting a custom entity detection job](#detecting-cer-api)
+ [Setting text extraction options](#detecting-cer-pdf)

**To create a custom entity recognition job**

1. Sign in to the AWS Management Console and open the [Amazon Comprehend console\.](https://console.aws.amazon.com/comprehend/home?region=us-east-1#api-explorer:)

1. From the left menu, choose **Analysis jobs** and then choose **Create job**\.

1. Give the classification job a name\. The name must be unique your account and current Region\.

1. Under **Analysis type**, choose **Custom entity recognition**\.

1. From **Recognizer model**, choose the custom entity recognizer to use\.

1. From **Version**, choose the recognizer version to use\.

1. \(Optional\) If you choose to encrypt the data in the storage volume while your entity recognition job is processed, choose **Job encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key ID under **KMS key ARN**\.
**Note**  
For more information on creating and using KMS keys and the associated encryption, see [Key management service \(KMS\)](https://docs.aws.amazon.com/kms/latest/developerguide/overview.html)\.

1. Under **Input data**, enter the location of the Amazon S3 bucket that contains your input documents or navigate to it by choosing **Browse S3**\. This bucket must be in the same region as the API that you are calling\. The IAM role you're using for access permissions for the classification job must have reading permissions for the S3 bucket\.

1. \(Optional\) Choose the format of the documents to be classified under **Input format**\. These can be one document per file, or one document per line in a single file\.

1. Under **Output data**, enter the location of the Amazon S3 bucket where Amazon Comprehend should write the job's output data or navigate to it by choosing **Browse S3**\. This bucket must be in the same region as the API that you are calling\. The IAM role you're using for access permissions for the classification job must have write permissions for the S3 bucket\.

1. \(Optional\) If you choose to encrypt the output result from your job, choose **Encryption** and then choose whether to use a KMS key associated with the current account, or one from another account\.
   + If you are using a key associated with the current account, choose the key alias or ID for **KMS key ID**\.
   + If you are using a key associated with a different account, enter the ARN for the key alias or ID under **KMS key ID**\.

1. \(Optional\) To launch your resources into Amazon Comprehend from a VPC, enter the VPC ID under **VPC** or choose the ID from the drop\-down list\. 

   1. Choose the subnet under **Subnet\(s\)**\. After you select the first subnet, you can choose additional ones\.

   1. Under **Security Group\(s\)**, choose the security group to use if you specified one\. After you select the first security group, you can choose additional ones\.
**Note**  
When you use a VPC with your analysis job, the `DataAccessRole` used for the Create and Start operations must have permissions to the VPC from which the output bucket are accessed\.

1. Choose **Create job** to create the entity recognition job\.



## Starting a custom entity detection job<a name="detecting-cer-api"></a>

To start a custom entity detection job with the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation, you must provide the EntityRecognizerArn, which is the Amazon Resource Name \(ARN\) of the trained model\. You can find this ARN in the response to the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation\. 

Use the following example for Unix, Linux, and macOS environments\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. To detect custom entities in a document set, use the following request syntax:

```
aws comprehend start-entities-detection-job \
       --entity-recognizer-arn "entity recognizer arn" \
       --job-name job name \
       --data-access-role-arn "data access role arn" \
       --language-code en \
       --input-data-config "S3Uri=s3://Bucket Name/Bucket Path" \
       --output-data-config "S3Uri=s3://Bucket Name/Bucket Path/" \
       --region region
```

Amazon Comprehend responds with the `JobID` and `JobStatus` and will return the output from the job in the S3 bucket that you specified in your request\.

**Example output from custom entity detection jobs for plain text and PDF documents**  

```
{
      "File": "50_docs",
      "Line": 0,
      "Entities":
      [
          {
              "BeginOffset": 0,
              "EndOffset": 22,
              "Score": 0.9763959646224976,
              "Text": "John Johnson",
              "Type": "JUDGE"
          }
      ]
  }
  {
      "File": "50_docs",
      "Line": 1,
      "Entities":
      [
          {
              "BeginOffset": 11,
              "EndOffset": 15,
              "Score": 0.9615424871444702,
              "Text": "Thomas Kincaid",
              "Type": "JUDGE"
          }
      ]
  }
```

```
{
      "Blocks":
      [
          {
              "BlockType": "LINE",
              "Geometry":
              {
                  "BoundingBox":
                  {
                      "Height": 0.012575757575757575,
                      "Left": 0.0,
                      "Top": 0.0015063131313131314,
                      "Width": 0.02262091503267974
                  },
                  "Polygon":
                  [
                      {
                          "X": 0.0,
                          "Y": 0.0015063131313131314
                      },
                      {
                          "X": 0.02262091503267974,
                          "Y": 0.0015063131313131314
                      },
                      {
                          "X": 0.02262091503267974,
                          "Y": 0.014082070707070706
                      },
                      {
                          "X": 0.0,
                          "Y": 0.014082070707070706
                      }
                  ]
              },
              "Id": "4330efed-6334-4fc4-ba48-e050afa95c8d",
              "Page": 1,
              "Relationships":
              [
                  {
                      "ids":
                      [
                          "f343ce48-583d-4abe-b84b-a232e266450f"
                      ],
                      "type": "CHILD"
                  }
              ],
              "Text": "S-3"
          },
          {
              "BlockType": "WORD",
              "Geometry":
              {
                  "BoundingBox":
                  {
                      "Height": 0.012575757575757575,
                      "Left": 0.0,
                      "Top": 0.0015063131313131314,
                      "Width": 0.02262091503267974
                  },
                  "Polygon":
                  [
                      {
                          "X": 0.0,
                          "Y": 0.0015063131313131314
                      },
                      {
                          "X": 0.02262091503267974,
                          "Y": 0.0015063131313131314
                      },
                      {
                          "X": 0.02262091503267974,
                          "Y": 0.014082070707070706
                      },
                      {
                          "X": 0.0,
                          "Y": 0.014082070707070706
                      }
                  ]
              },
              "Id": "f343ce48-583d-4abe-b84b-a232e266450f",
              "Page": 1,
              "Relationships":
              [],
              "Text": "S-3"
          }
      ],
      "DocumentMetadata":
      {
          "PageNumber": 1,
          "Pages": 1
      },
      "DocumentType": "NativePDF",
      "Entities":
      [
          {
              "BlockReferences":
              [
                  {
                      "BeginOffset": 25,
                      "BlockId": "4330efed-6334-4fc4-ba48-e050afa95c8d",
                      "ChildBlocks":
                      [
                          {
                              "BeginOffset": 1,
                              "ChildBlockId": "cbba5534-ac69-4bc4-beef-306c659f70a6",
                              "EndOffset": 6
                          }
                      ],
                      "EndOffset": 30
                  }
              ],
              "Score": 0.9998825926329088,
              "Text": "0.001",
              "Type": "OFFERING_PRICE"
          },
          {
              "BlockReferences":
              [
                  {
                      "BeginOffset": 41,
                      "BlockId": "f343ce48-583d-4abe-b84b-a232e266450f",
                      "ChildBlocks":
                      [
                          {
                              "BeginOffset": 0,
                              "ChildBlockId": "292a2e26-21f0-401b-a2bf-03aa4c47f787",
                              "EndOffset": 9
                          }
                      ],
                      "EndOffset": 50
                  }
              ],
              "Score": 0.9809727537330395,
              "Text": "6,097,560",
              "Type": "OFFERED_SHARES"
          }
      ],
      "File": "example.pdf",
      "Version": "2021-04-30"
  }
```

## Setting text extraction options<a name="detecting-cer-pdf"></a>

If your input files include image files, PDFs, or Word documents, you can specify options for text extraction\. In the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation, configure the `DocumentReaderConfig` parameter in `InputDataConfig` to specify the following options :
+ **DocumentReadMode** – If you set to `SERVICE_DEFAULT`, Amazon Comprehend automatically selects the text extraction actions based on the input document types\. If you set to `FORCE_DOCUMENT_READ_ACTION`, Amazon Comprehend uses the Amazon Textract APIs to parse PDF, Word, or image files\.
+ **DocumentReadAction** – Set to `TEXTRACT_DETECT_DOCUMENT_TEXT` for Amazon Comprehend to invoke the Amazon Textract `DetectDocumentText` API\. Set to `TEXTRACT_ANALYZE_DOCUMENT` for Amazon Comprehend to invoke the Amazon Textract `AnalyzeDocument` API\.

If you set **DocumentReadMode** to `SERVICE_DEFAULT`, you do not need to configure **DocumentReadAction**\. 

You can pass the `InputDataConfig` parameter to `StartEntitiesDetectionJob` as a JSON file\. The following example shows a JSON file to use the `DetectDocumentText` API:

**Example `InputDataConfig` Parameters in file myInputDataConfig\.json**  

```
"InputDataConfig": {
  "S3Uri": s3://Bucket Name/Bucket Path",
  "InputFormat": "ONE_DOC_PER_FILE",
  "DocumentReaderConfig": {
      "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT",
      "DocumentReadMode": "FORCE_DOCUMENT_READ_ACTION"
  }
}
```

In the `StartEntitiesDetectionJob` operation, specify the parameter as a file:

```
  --input-data-config file://myInputDataConfig.json  
```

For more information about the Amazon Textract options, see [DocumentReaderConfig](API_DocumentReaderConfig.md)\.