# Running a Classification Job<a name="how-class-run"></a>

Once you've trained your model, your custom classifier is available for use in categorizing unlabeled documents\. 

For Amazon Comprehend to process them, all documents must be in UTF\-8\-formatted text files\. You can submit your documents in two formats\. The format you use depends on the type of documents you want to analyze, as described below\.


| Description | Format | 
| --- | --- | 
| Each file contains one input document\. This is best for collections of large documents, such as newspaper articles or scientific papers\. | One document per file | 
|  The input is one or more files\. Each line in a file is considered a document\. This is best for short documents, such as text messages or social media posts\. Each line must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. You can't use the UTF\-8 line separator \(u\+2028\) to end a line\.  | One document per line | 

**One document per line**

With the `One document per line` method, each document is placed on a separate line and no header is used\. The label is not included on each line \(since you don't yet know the label for the document\)\. Each line of the file \(the end of the individual document\) must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\.

The format of the input file can be seen as thus:

```
Text of document 1 \n
Text of document 2 \n
Text of document 3 \n
Text of document 4 \n
```

After preparing the documents file, you place that file in the S3 bucket that you're using for input data\.

**One Document per File**

As with the previous method, the files used for this must be UTF\-8 formatted text files\. Each of thse is placed into the S3 bucket being used for input data\.

The input data bucket contains the files used to run the classification job\. Each file represents one document\. 

When you start a classification job, you will specify this S3 location for your input data\. The URI must be in the same AWS Region as the API endpoint that you are calling\. The URI can point to a single file \(as when using the "one document per line" method, or it can be the prefix for a collection of data files\. 

For example, if you use the URI S3://bucketName/prefix, if the prefix is a single file, Amazon Comprehend uses that file as input\. If more than one file begins with the prefix, Amazon Comprehend uses all of them as input\. 

You must grant Amazon Comprehend access to the Amazon S3 bucket that contains your document collection and output files\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## The Classification Job<a name="the-class-job"></a>

Use the [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) operation to start classifying unlabeled documents\. You provide the S3 bucket that contains the documents to be classified, the S3 bucket where the output should be placed, and classifier to use\.

Custom classification is asynchronous\. Once you have started the job, use the [DescribeDocumentClassificationJob](API_DescribeDocumentClassificationJob.md) operation to monitor its progress\. When the `Status` field in the response shows `COMPLETED`, you can access the output in the location that you specified\.

The output is a single file named `output.tar.gz`\. It is a compressed archive file that contain a text file with the output\. 

If you input was one document per line, the output file contains one line for each line in the input\. Each line has the file name, the zero\-based line number of the input line, the class label assigned to the document, and the confidence that Amazon Comprehend has that the file was correctly classified\.

For example:

```
{"File": "file1.txt", "Line": "0", "Classes": [{"Name": "Cats", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Fluffy Animals", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "1", "Classes": [{"Name": "Dogs", "Score": 0.5}, {"Name": "Dogs", "Score": 0.0381}, {"Name": "Dogs", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "2", "Classes": [{"Name": "Cats", "Score": 0.1}, {"Name": "Cats", "Score": 0.0381}, {"Name": "Cats", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "3", "Classes": [{"Name": "Fluffy Animals", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

If your input was one document per file, the output file contains one line for each document\. Each line has the name of the file, the label of the class the file was assigned, and the confidence that Amazon Comprehend has that the file was correctly classified\.

For example:

```
{"File": "file1.txt", "Classes": [{"Name": "Cats", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Fluffy Animals", "Score": 0.0372}]}
{"File": "file1.txt", "Classes": [{"Name": "Dogs", "Score": 0.5}, {"Name": "Dogs", "Score": 0.0381}, {"Name": "Dogs", "Score": 0.0372}]}
{"File": "file2.txt", "Classes": [{"Name": "Cats", "Score": 0.1}, {"Name": "Cats", "Score": 0.0381}, {"Name": "Cats", "Score": 0.0372}]}
{"File": "file2.txt", "Classes": [{"Name": "Fluffy Animals", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

**Note**  
For more information about the asynchronous analysis job format, see [Asynchronous Batch Processing](how-async.md) 