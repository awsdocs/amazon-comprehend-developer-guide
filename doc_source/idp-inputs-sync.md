# Inputs for real\-time custom analysis<a name="idp-inputs-sync"></a>

Real\-time analysis using custom models takes a single document as input\. The following topics describe the input document types that you can use\.

**Topics**
+ [Plain text documents](#idp-inputs-sync-text)
+ [Semi\-structured documents](#idp-inputs-sync-semi)
+ [Image files and scanned PDF files](#idp-inputs-sync-ocr)
+ [Amazon Textract output](#idp-inputs-sync-textract)
+ [Maximum document sizes for real\-time analysis](#idp-inputs-sync-sizes)
+ [Errors in semi\-structured documents](#idp-inputs-sync-err)

## Plain text documents<a name="idp-inputs-sync-text"></a>

Provide the input document as UTF\-8\-formatted text\. 

## Semi\-structured documents<a name="idp-inputs-sync-semi"></a>

Semi\-structured documents include native PDF documents and Word documents\. 

By default, real\-time custom analysis uses the Amazon Comprehend parser to extract the text from Word files and digital PDF files\. For PDF files, you can override this default and use Amazon Textract to extract the text\. See [Setting text extraction options](idp-set-textract-options.md)\.

## Image files and scanned PDF files<a name="idp-inputs-sync-ocr"></a>

Supported image types include JPEG, PNG, and TIFF\.

By default, custom entity recognition uses the Amazon Textract `DetectDocumentText` API operation to extract the text from image files and scanned PDF files\. You can override this default to use the `AnalyzeDocument` API operation instead\. See [Setting text extraction options](idp-set-textract-options.md)\.

## Amazon Textract output<a name="idp-inputs-sync-textract"></a>

You can provide the JSON output from the Amazon Textract `DetectDocumentText` API or `AnalyzeDocument` API as input to the real\-time API operations for custom classification and custom entity recognition\. Amazon Comprehend supports this input type for the real\-time API operations, but not for the console\.

## Maximum document sizes for real\-time analysis<a name="idp-inputs-sync-sizes"></a>

For all input document types, the input file maximum is one page, with no more than 10,000 characters\.

The following table shows the maximum file sizes for input documents\. 


| File type | Maximum size \(API\) | Maximum size \(console\) | 
| --- | --- | --- | 
| UTF\-8 text documents | 10 KB | 10 KB | 
| PDF documents | 10 MB | 5 MB | 
| Word documents | 10 MB | 5 MB | 
| Image files | 10 MB | 5 MB | 
| Textract output files | 1 MB | n/a | 

## Errors in semi\-structured documents<a name="idp-inputs-sync-err"></a>

 The [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) or [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) API operation can encounter document\-level or page\-level errors while extracting text from a semi\-structured document or an image file\.

### Page\-level errors<a name="idp-inputs-sync-page-err"></a>

 If the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) or [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) API operation encounters errors while processing a page in the input document, the API response includes an entry in the [Errors list](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ErrorsListItem.html) for each error\.

The `ErrorCode` in the error list entry contains one of the following values:
+ TEXTRACT\_BAD\_PAGE – Amazon Textract cannot read the page\. For more information about page limits in Amazon Textract, see [ Page Quotas in Amazon Textract](https://docs.aws.amazon.com/textract/latest/dg/limits-document.html)\.
+ TEXTRACT\_PROVISIONED\_THROUGHPUT\_EXCEEDED – The number of requests exceeded your throughput limit\. For more information about throughput quotas in Amazon Textract, see [ Default quotas in Amazon Textract](https://docs.aws.amazon.com/textract/latest/dg/limits-quotas-explained.html)\.
+ PAGE\_CHARACTERS\_EXCEEDED – Too many text characters on the page \(10,000 characters maximum\)\.
+ PAGE\_SIZE\_EXCEEDED – The maximum page size is 10 MB\.
+ INTERNAL\_SERVER\_ERROR – The request encountered a service issue\. Try the API request again\.

### Document\-level errors<a name="idp-inputs-sync-doc-err"></a>

If the [ClassifyDocument](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_ClassifyDocument.html) or [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html) API operation detects a document\-level error in your input document, the API returns an `InvalidRequestException` error response\. 

In the error response, the Reason field contains the value `INVALID_DOCUMENT`\. 

The Detail field contains one of the following values:
+ DOCUMENT\_SIZE\_EXCEEDED – Document size is too large\. Check the size of your file and resubmit the request\.
+ UNSUPPORTED\_DOC\_TYPE – Document type is not supported\. Check the file type and resubmit the request\.
+ PAGE\_LIMIT\_EXCEEDED – Too many pages in the document\. Check the number of pages in your file and resubmit the request\.
+ TEXTRACT\_ACCESS\_DENIED\_EXCEPTION – Access denied to Amazon Textract\. Verify that your account has permission to use the Amazon Textract [DetectDocumentText](https://docs.aws.amazon.com/textract/latest/dg/API_DetectDocumentText.html) and [AnalyzeDocument](https://docs.aws.amazon.com/textract/latest/dg/API_AnalyzeDocument.html) API operations and resubmit the request\.