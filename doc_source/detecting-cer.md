# Detecting Custom Entities with an Asynchronous Batch Job with Amazon Comprehend<a name="detecting-cer"></a>

Once you have a trained model, use the [StartEntitiesDetectionJob](API_StartEntitiesDetectionJob.md) operation to detect custom entities in your documents\. 

**Before you begin**  
Before you can detect custom entities, you must have a custom entity recognition model\. For more information about these models, see [Training custom entity recognizers](training-recognizers.md)\. For the steps to train a model, see [Creating a Custom Entity Recognizer Using the Console \- CSV Format](getting-started-custom-entity-recognizer.md#getting-started-console-CER)\.

Using this operation, you provide the same information as you would when detecting preset entities\. However, in addition to the input and output locations \(S3 buckets\), you also provide the EntityRecognizerArn, which is the Amazon Resource Name \(ARN\) of the trained model\. This ARN is supplied by the response to the [CreateEntityRecognizer](API_CreateEntityRecognizer.md) operation\. 

You can examine one document or many, and each model can be trained on up to 25 custom entities at a time\. You can search for up to 25 entities per **StartEntitiesDetectionJob** operation\. 

Use the following example for Unix, Linux, and macOS\. For Windows, replace the backslash \(\\\) Unix continuation character at the end of each line with a caret \(^\)\. To detect custom entities in a document set, use the following request syntax:

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

**Example Output from custom entity detection jobs for plain text and PDF documents**  

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