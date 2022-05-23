# Running custom recognizer models<a name="detecting-recognizers"></a>

After you train your custom recognizer model, you can run real\-time or asynchronous custom entity recognition\. You need to create an endpoint to run real\-time analysis using a custom model\.

**Before you begin**  
You need a custom entity recognition model \(also known as a recognizer\) before you can detect custom entities\. A recognizer that is trained with plain\-text annotations supports entity detection for plain\-text documents only\. A recognizer that is trained with PDF document annotations supports entity detection for plain\-text documents, images, PDF files, and Word documents\.  
For more information about these models, see [Training recognizer models](training-recognizers.md)\. 

**Topics**
+ [Best practices for image files](#detecting-recognizers-image-bp)
+ [Real\-time analysis for custom entity recognition \(console\)](detecting-cer-real-time.md)
+ [Analysis jobs for custom entity recognition \(console\)](detecting-cer.md)

## Best practices for image files<a name="detecting-recognizers-image-bp"></a>

To analyze image files for custom entity recognition, use the following guidelines to achieve the best results:
+ Provide a high quality image, ideally at least 150 DPI\.
+ If the input document is already in one of the supported file formats \(TIFF, JPEG, or PNG for images\), don't convert or downsample the document before uploading it to Amazon S3\.

For the best results when extracting text from tables in documents, ensure that:
+ Tables in your document are visually separated from surrounding elements on the page\. For example, the table isn't overlaid onto an image or complex pattern\.
+ Text within the table is upright\. For example, the text isn't rotated relative to other text on the page\.

When extracting text from tables, you might see inconsistent results when: 
+ Merged table cells span multiple columns\.
+ Tables have cells, rows, or columns that are different than other parts of the same table\.