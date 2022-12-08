# Best practices for images<a name="idp-images-bp"></a>

When you use image files for custom classification or custom entity recognition, use the following guidelines to achieve the best results:
+ Provide a high quality image, ideally at least 150 DPI\.
+ If the image file uses one of the supported formats \(TIFF, JPEG, or PNG\), don't convert or downsample the file before uploading it to Amazon S3\.

For the best results when extracting text from tables in documents, follow these practices:
+ Tables in your document are visually separated from surrounding elements on the page\. For example, the table isn't overlaid onto an image or complex pattern\.
+ Text within the table is upright\. For example, the text isn't rotated relative to other text on the page\.

When extracting text from tables, you might see inconsistent results for the following cases: 
+ Merged table cells span multiple columns\.
+ Tables have cells, rows, or columns that are different than other parts of the same table\.