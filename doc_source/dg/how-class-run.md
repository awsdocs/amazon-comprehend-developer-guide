# Running an Asynchronous Classification Job<a name="how-class-run"></a>

After you've trained your model, your custom classifier is available for asynchronous use to categorize unlabeled documents\. 

**Note**  
If trained in multi\-class mode, your customer classifier can also be used for real\-time insights into documents\. However, real\-time analysis can only be applied to a single document at a time\. For more information, see [Real\-time Analysis with Custom Classification](custom-sync.md)\.

For asynchronous analysis, all documents must be in UTF\-8\-formatted text files\. Although you can only train your custom classification model using the `one document per line` format, you can submit your documents in that format or as `one document per file`\. The format you use depends on the type of documents you want to analyze, as described below\.


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

As with the previous method, the files used for this must be UTF\-8 formatted text files\. Each of these is placed into the S3 bucket being used for input data\.

The input data bucket contains the files used to run the classification job\. Each file represents one document\. 

When you start a classification job, you will specify this Amazon S3 location for your input data\. The URI must be in the same AWS Region as the API endpoint that you are calling\. The URI can point to a single file \(as when using the "one document per line" method, or it can be the prefix for a collection of data files\. 

For example, if you use the URI `S3://bucketName/prefix`, if the prefix is a single file, Amazon Comprehend uses that file as input\. If more than one file begins with the prefix, Amazon Comprehend uses all of them as input\. 

Grant Amazon Comprehend access to the S3 bucket that contains your document collection and output files\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.

## The Classification Job<a name="the-class-job"></a>

Use the [StartDocumentClassificationJob](API_StartDocumentClassificationJob.md) operation to start classifying unlabeled documents\. You provide the S3 bucket that contains the documents to be classified, the S3 bucket where the output should be placed, and classifier to use\.

Custom classification is asynchronous\. Once you have started the job, use the [DescribeDocumentClassificationJob](API_DescribeDocumentClassificationJob.md) operation to monitor its progress\. When the `Status` field in the response shows `COMPLETED`, you can access the output in the location that you specified\.

### Classification Job Output<a name="class-output"></a>

For asynchronous analysis, all documents must be in UTF\-8\-formatted text files\. Although you can only train your custom classification model using the `one document per line` format, you can submit your documents in that format or as `one document per file`\. The format you use depends on the type of documents you want to analyze, as described below\.

The output from your classification job depends not only on the dataset you use\. The output also depends on whether the classifier you use was trained for multi\-class or multi\-label mode\. Inference \(the classification job\) is directly dependent on the classifier model training mode used\.

Regardless of the mode used, the job output consists of a single file named `output.tar.gz`\. It is a compressed archive file that contains a text file with the output\. 

**Multi\-Class Output**

When you use a classifier trained in multi\-class mode, your results are shown in terms of `classes`\. Each of these `classes` is the class used to create the set of categories when training your classifier\.

The following examples use the following mutually exclusive classes\.

```
DOCUMENTARY
SCIENCE_FICTION
ROMANTIC_COMEDY
SERIOUS_DRAMA
OTHER
```

If your input data is formatted as one document per line, the output file contains one line for each line in the input\. Each line has the file name, the zero\-based line number of the input line, the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file1.txt", "Line": "0", "Classes": [{"Name": "Documentary", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Serious_Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "1", "Classes": [{"Name": "Science_Fiction", "Score": 0.5}, {"Name": "Science_Fiction", "Score": 0.0381}, {"Name": "Science_Fiction", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "2", "Classes": [{"Name": "Documentary", "Score": 0.1}, {"Name": "Documentary", "Score": 0.0381}, {"Name": "Documentary", "Score": 0.0372}]}
{"File": "file2.txt", "Line": "3", "Classes": [{"Name": "Serious_Drama", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

If your input data is formatted as one document per file, the output file contains one line for each document\. Each line has the name of the file and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file0.txt", "Classes": [{"Name": "Documentary", "Score": 0.8642}, {"Name": "Other", "Score": 0.0381}, {"Name": "Serious_Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Classes": [{"Name": "Science_Fiction", "Score": 0.5}, {"Name": "Science_Fiction", "Score": 0.0381}, {"Name": "Science_Fiction", "Score": 0.0372}]}
{"File": "file2.txt", "Classes": [{"Name": "Documentary", "Score": 0.1}, {"Name": "Documentary", "Score": 0.0381}, {"Name": "Domentary", "Score": 0.0372}]}
{"File": "file3.txt", "Classes": [{"Name": "Serious_Drama", "Score": 0.3141}, {"Name": "Other", "Score": 0.0381}, {"Name": "Other", "Score": 0.0372}]}
```

**Multi\-Label Output**

When you use a classifier trained in multi\-label mode, your results are shown in terms of `labels`\. Each of these `labels` is the labels used to create the set of categories when training your classifier\.

The following examples use these unique labels\.

```
SCIENCE_FICTION
ACTION
DRAMA
COMEDY
ROMANCE
```

If your input data is formatted as one document per line, the output file contains one line for each line in the input\. Each line has the file name, the zero\-based line number of the input line, the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file1.txt", "Line": "0", "Labels": [{"Name": "Action", "Score": 0.8642}, {"Name": "Drama", "Score": 0.650}, {"Name": "Science Fiction", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "1", "Labels": [{"Name": "Comedy", "Score": 0.5}, {"Name": "Action", "Score": 0.0381}, {"Name": "Drama", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "2", "Labels": [{"Name": "Action", "Score": 0.9934}, {"Name": "Drama", "Score": 0.0381}, {"Name": "Action", "Score": 0.0372}]}
{"File": "file1.txt", "Line": "3", "Labels": [{"Name": "Romance", "Score": 0.9845}, {"Name": "Comedy", "Score": 0.8756}, {"Name": "Drama", "Score": 0.7723}, {"Name": "Science_Fiction", "Score": 0.6157}]}
```

If your input data is formatted as one document per file, the output file contains one line for each document\. Each line has the name of the file and the class or classes found in the document\. It ends with the confidence that Amazon Comprehend has that the individual instance was correctly classified\.

For example:

```
{"File": "file0.txt", "Labels": [{"Name": "Action", "Score": 0.8642}, {"Name": "Drama", "Score": 0.650}, {"Name": "Science Fiction", "Score": 0.0372}]}
{"File": "file1.txt", "Labels": [{"Name": "Comedy", "Score": 0.5}, {"Name": "Action", "Score": 0.0381}, {"Name": "Drama", "Score": 0.0372}]}
{"File": "file2.txt", "Labels": [{"Name": "Action", "Score": 0.9934}, {"Name": "Drama", "Score": 0.0381}, {"Name": "Action", "Score": 0.0372}]}
{"File": "file3.txt”, "Labels": [{"Name": "Romance", "Score": 0.9845}, {"Name": "Comedy", "Score": 0.8756}, {"Name": "Drama", "Score": 0.7723}, {"Name": "Science_Fiction", "Score": 0.6157}]}
```

**Note**  
For more information about the asynchronous analysis job format, see [Asynchronous Batch Processing](how-async.md) 