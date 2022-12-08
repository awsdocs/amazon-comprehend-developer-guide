# Inputs for asynchronous custom analysis<a name="idp-inputs-async"></a>

You can input multiple documents to a custom async analysis job\. The following topics describe the input document types that you can use\. The maximum file size varies depending on the type of input document\. 

**Topics**
+ [Plain text documents](#idp-inputs-async-text)
+ [Semi\-structured documents](#idp-inputs-async-semi)
+ [Image files and scanned PDF files](#idp-inputs-async-ocr)
+ [Amazon Textract output JSON files](#idp-inputs-async-textract)

## Plain text documents<a name="idp-inputs-async-text"></a>

Provide all plain\-text input documents as UTF\-8\-formatted text\. The following table lists the maximum file sizes and other guidelines\. 

**Note**  
These limits apply when **all** the input files are plain text\.


| Description | Quota/Guideline | 
| --- | --- | 
| Maximum file size for one document per file format \(Custom classification\) | 1 byte–10 MB | 
| Document size \(Custom entity recognition\) | 1 byte–1 MB | 
| Maximum number of files, one document per file | 1,000,000 | 
| Maximum number of lines, one document per line \(for all files in request\) | 1,000,000 | 
| Document corpus size \(all docs in plaintext combined\) | 1 byte–5 GB | 

## Semi\-structured documents<a name="idp-inputs-async-semi"></a>

Semi\-structured documents include native PDF documents and Word documents\. 

The following table lists the maximum file sizes and other guidelines\.


| Description | Quota/Guideline | 
| --- | --- | 
| Document size \(PDF\) | 1 byte–50 MB | 
| Document size \(Docx\) | 1 byte–5 MB | 
| Maximum number of files | 500 | 
| Maximum number of pages for a PDF or Docx file | 100 | 
| Document corpus size after text extraction \(plaintext, all files combined\) | 1 byte–5 GB | 

By default, custom analysis uses the Amazon Comprehend parser to extract the text from Word files and digital PDF files\. For PDF files, you can override this default and use Amazon Textract to extract the text\. See [Setting text extraction options](idp-set-textract-options.md)\.

## Image files and scanned PDF files<a name="idp-inputs-async-ocr"></a>

Custom analysis supports JPEG, PNG, and TIFF images\.

The following table lists the maximum file sizes for images\. Scanned PDF files are subject to the same maximum sizes as native PDF files\.


| Description | Quota/Guideline | 
| --- | --- | 
| Image size \(JPG or PNG\) | 1 byte–10 MB | 
| Image size \(TIFF\) | 1 byte–10 MB\. Maximum one page\. | 

For additional information about images, see [Best practices for images](idp-images-bp.md)\.

By default, Amazon Comprehend uses the Amazon Textract `DetectDocumentText` API operation to extract the text from image files and scanned PDF files\. You can override this default to use the `AnalyzeDocument` API operation instead\. See [Setting text extraction options](idp-set-textract-options.md)\.

## Amazon Textract output JSON files<a name="idp-inputs-async-textract"></a>

For custom entity recognition, but not custom classification, you can provide the output file from the Amazon Textract `AnalyzeDocument` API operation as input to analysis jobs\. 