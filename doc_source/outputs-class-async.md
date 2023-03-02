# Outputs for asynchronous analysis jobs<a name="outputs-class-async"></a>

After an analysis job completes, it stores the results in the S3 bucket that you specified in the request\.

## Outputs for text inputs<a name="outputs-class-async-text"></a>

For either format of text input documents \(multi\-class or multi\-label\), the job output consists of a single file named `output.tar.gz`\. It's a compressed archive file that contains a text file with the output\. 

**Multi\-class output**

When you use a classifier trained in multi\-class mode, your results show `classes`\. Each of these `classes` is the class used to create the set of categories when training your classifier\.

For more details about these output fields, see [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) in the *Amazon Comprehend API Reference*\.

The following examples use the following mutually exclusive classes\.

```
DOCUMENTARY
SCIENCE_FICTION
ROMANTIC_COMEDY
SERIOUS_DRAMA
OTHER
```

If your input data format is one document per line, the output file contains one line for each line in the input\. Each line includes the file name, the zero\-based line number of the input line, and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file1.txt", "Line": "0", "Classes": [{"Name": "Documentary", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Serious_Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "1", "Classes": [{"Name": "Science_Fiction", "Score": 0.5}, {"Name": "Science_Fiction", "Score": 0.0381}, {"Name": "Science_Fiction", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "2", "Classes": [{"Name": "Documentary", "Score": 0.1}, {"Name": "Documentary", "Score": 0.0381}, {"Name": "Documentary", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "3", "Classes": [{"Name": "Serious_Drama", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

If your input data format is one document per file, the output file contains one line for each document\. Each line has the name of the file and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend classified the individual instance accurately\.

For example:

```
{"File": "file0.txt", "Classes": [{"Name": "Documentary", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Serious_Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Classes": [{"Name": "Science_Fiction", "Score": 0.5}, {"Name": "Science_Fiction", "Score": 0.0381}, {"Name": "Science_Fiction", "Score": 0.0372}]}
{"File": "file2.txt", "Classes": [{"Name": "Documentary", "Score": 0.1}, {"Name": "Documentary", "Score": 0.0381}, {"Name": "Domentary", "Score": 0.0372}]}
{"File": "file3.txt", "Classes": [{"Name": "Serious_Drama", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

**Multi\-label output**

When you use a classifier trained in multi\-label mode, your results show `labels`\. Each of these `labels` is the label used to create the set of categories when training your classifier\.

The following examples use these unique labels\.

```
SCIENCE_FICTION
ACTION
DRAMA
COMEDY
ROMANCE
```

If your input data format is one document per line, the output file contains one line for each line in the input\. Each line includes the file name, the zero\-based line number of the input line, and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file1.txt", "Line": "0", "Labels": [{"Name": "Action", "Score": 0.8642}, {"Name": "Drama", "Score": 0.650}, {"Name": "Science Fiction", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "1", "Labels": [{"Name": "Comedy", "Score": 0.5}, {"Name": "Action", "Score": 0.0381}, {"Name": "Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "2", "Labels": [{"Name": "Action", "Score": 0.9934}, {"Name": "Drama", "Score": 0.0381}, {"Name": "Action", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "3", "Labels": [{"Name": "Romance", "Score": 0.9845}, {"Name": "Comedy", "Score": 0.8756}, {"Name": "Drama", "Score": 0.7723}, {"Name": "Science_Fiction", "Score": 0.6157}]}
```

If your input data format is one document per file, the output file contains one line for each document\. Each line has the name of the file and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend classified the individual instance accurately\.

For example:

```
{"File": "file0.txt", "Labels": [{"Name": "Action", "Score": 0.8642}, {"Name": "Drama", "Score": 0.650}, {"Name": "Science Fiction", "Score": 0.0372}]}
{"File": "file1.txt", "Labels": [{"Name": "Comedy", "Score": 0.5}, {"Name": "Action", "Score": 0.0381}, {"Name": "Drama", "Score": 0.0372}]}
{"File": "file2.txt", "Labels": [{"Name": "Action", "Score": 0.9934}, {"Name": "Drama", "Score": 0.0381}, {"Name": "Action", "Score": 0.0372}]}
{"File": "file3.txt”, "Labels": [{"Name": "Romance", "Score": 0.9845}, {"Name": "Comedy", "Score": 0.8756}, {"Name": "Drama", "Score": 0.7723}, {"Name": "Science_Fiction", "Score": 0.6157}]}
```

## Outputs for semi\-structured input documents<a name="outputs-class-async-other"></a>

For semi\-structured input documents, the output can include the following additional fields:
+ DocumentMetadata – Extraction information about the document\. The metadata includes a list of pages in the document, with the number of characters extracted from each page\. This field is present in the response if the request included the `Byte` parameter\.
+ DocumentType – The document type for each page in the input document\. This field is present in the response if the request included the `Byte` parameter\.
+ Errors – Page\-level errors that the system detected while processing the input document\. The field is empty if the system encountered no errors\.

For more details about these output fields, see [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) in the *Amazon Comprehend API Reference*\.

The following example shows output for a two\-page scanned PDF file\.

```
[{ #First page output
    "Classes": [
        {
            "Name": "__label__2 ",
            "Score": 0.9993996620178223
        },
        {
            "Name": "__label__3 ",
            "Score": 0.0004330444789957255
        }
    ],
    "DocumentMetadata": {
        "PageNumber": 1,
        "Pages": 2
    },
    "DocumentType": "ScannedPDF",
    "File": "file.pdf",
    "Version": "VERSION_NUMBER"
},
#Second page output
{
    "Classes": [
        {
            "Name": "__label__2 ",
            "Score": 0.9993996620178223
        },
        {
            "Name": "__label__3 ",
            "Score": 0.0004330444789957255
        }
    ],
    "DocumentMetadata": {
        "PageNumber": 2,
        "Pages": 2
    },
    "DocumentType": "ScannedPDF",
    "File": "file.pdf",
    "Version": "VERSION_NUMBER" 
}]
```