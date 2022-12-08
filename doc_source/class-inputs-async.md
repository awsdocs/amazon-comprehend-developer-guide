# File formats for async analysis<a name="class-inputs-async"></a>

You train your custom classification models using text files in `one document per line` format\.

However, when you run async analysis with your model, you have a choice of formats for input documents: `One document per line` or `one document per file`\. The format you use depends on the type of documents you want to analyze, as described in the following table\.


| Description | Format | 
| --- | --- | 
| The input contains multiple files\. Each file contains one input document\. This format is best for collections of large documents, such as newspaper articles or scientific papers\. Also, use this format for semi\-structured documents \(image, PDF, or Docx files\) using a plain\-text classifier\. | One document per file | 
|  The input is one or more files\. Each line in the file is a separate input document\. This format is best for short documents, such as text messages or social media posts\.  | One document per line | 

**One document per file**

With `one document per file` format, each file represents one input document\. 

**One document per line**

With the `One document per line` format, each document is placed on a separate line and no header is used\. The label is not included on each line \(since you don't yet know the label for the document\)\. Each line of the file \(the end of the individual document\) must end with a line feed \(LF, \\n\), a carriage return \(CR, \\r\), or both \(CRLF, \\r\\n\)\. Don't use the UTF\-8 line separator \(u\+2028\) to end a line\.

The following example shows the format of the input file\.

```
Text of document 1 \n
Text of document 2 \n
Text of document 3 \n
Text of document 4 \n
```

For either format, use UTF\-8 encoding for text files\. After you prepare the files, place them in the S3 bucket that you're using for input data\.

When you start a classification job, you specify this Amazon S3 location for your input data\. The URI must be in the same Region as the API endpoint that you are calling\. The URI can point to a single file \(as when using the "one document per line" method, or it can be the prefix for a collection of data files\. 

For example, if you use the URI `S3://bucketName/prefix`, if the prefix is a single file, Amazon Comprehend uses that file as input\. If more than one file begins with the prefix, Amazon Comprehend uses all of them as input\. 

Grant Amazon Comprehend access to the S3 bucket that contains your document collection and output files\. For more information, see [Role\-based permissions required for asynchronous operations](access-control-managing-permissions.md#auth-role-permissions)\.