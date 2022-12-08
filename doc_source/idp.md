# Document processing<a name="idp"></a>

Amazon Comprehend supports one\-step document processing for custom classification and custom entity recognition\. For example, you can input a mix of plain text documents and semi\-structured documents \(such as PDF documents, Microsoft Word documents, and images\) to a custom analysis job\.

For input files that require text extraction, Amazon Comprehend automatically performs the text extraction before running the analysis\. To extract the text content, Amazon Comprehend uses an internal parser for semi\-structured documents and uses Amazon Textract APIs for images and scanned documents\. 

The following topics provide details about the input document types that Amazon Comprehend supports for custom analysis\.

**Topics**
+ [Inputs for real\-time custom analysis](idp-inputs-sync.md)
+ [Inputs for asynchronous custom analysis](idp-inputs-async.md)
+ [Setting text extraction options](idp-set-textract-options.md)
+ [Best practices for images](idp-images-bp.md)