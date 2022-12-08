# Outputs for asynchronous analysis jobs<a name="outputs-cer-async"></a>

After an analysis job completes, it stores the results in the S3 bucket that you specified in the request\.

## Outputs for text inputs<a name="outputs-cer-async-text"></a>

For text input files, the output consists of a list of entities for each input document\.

The following example shows the output for two documents from an input file named 50\_docs, using one document per line format\.

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

## Outputs for semi\-structured inputs<a name="outputs-cer-async-other"></a>

For semi\-structured input documents, the output can include the following additional fields:
+ DocumentMetadata – Extraction information about the document\. The metadata includes a list of pages in the document, with the number of characters extracted from each page\. This field is present in the response if the request included the `Byte` parameter\.
+ DocumentType – The document type for each page in the input document\. This field is present in the response for a request that included the `Byte` parameter\.
+ Blocks – Information about each block of text in the input document\. Blocks can nest within a block\. A page block contains a block for each line of text, which contains a block for each word\. This field is present in the response for a request that included the `Byte` parameter\.
+ BlockReferences – A reference to each block for this entity\. This field is present in the response for a request that included the `Byte` parameter\. The field isn't present for text files\.
+ Errors – Page\-level errors that the system detected while processing the input document\. The field is empty if the system encountered no errors\.

For more details about these output fields, see [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) in the Amazon Comprehend API Reference

The following example shows the output for a one\-page native PDF input document\.

**Example output from a custom entity recognition analysis of a PDF document**  

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