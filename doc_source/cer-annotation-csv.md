# CSV files \(plain text only\)<a name="cer-annotation-csv"></a>

When using comma\-separated value \(CSV\) files for your annotations, your CSV files must have the following columns:


| File | Line | Begin offset | End offset | Type | 
| --- | --- | --- | --- | --- | 
|  The name of the file containing the document\. For example, if one of the document files is located at `s3://my-S3-bucket/test-files/documents.txt`, the value in the `File` column will be `documents.txt`\. You must include the file extension \(in this case '`.txt`'\) as part of the file name\.  |  The line number containing the entity, starting with line 0\.  |  The character offset in the input text \(relative to the beginning of the line\) that shows where the entity begins\. The first character is at position 0\.  |  The character offset in the input text that shows where the entity ends\.  |  The customer\-defined entity type\. Entity types must be an uppercase, underscore\-separated string\. We recommend using descriptive entity types such as `MANAGER`, `SENIOR_MANAGER`, or `PRODUCT_CODE`\. Up to 25 entity types can be trained per model\.  | 

Here's an example:

The file `documents.txt` contains four lines \(rows 0, 1, 2, and 3\):

```
Diego Ramirez is an engineer in the high tech industry.
Emilio Johnson has been an engineer for 14 years.
J Doe is a judge on the Washington Supreme Court.
Our latest new employee, Mateo Jackson, has been a manager in the industry for 4 years.
```

The CSV file with the list of annotations is as follows: 

```
File, Line, Begin Offset, End Offset, Type
documents.txt, 0, 0, 13, ENGINEER
documents.txt, 1, 0, 15, ENGINEER
documents.txt, 3, 25, 38, MANAGER
```

**Note**  
In the annotations file, the line number containing the entity starts with line 0\. In this example, line 2 is not present in the CSV file because there is no entity in line 2 of `documents.txt`\.

**Creating your data files**

It's important to put your annotations in a properly configured CSV file to reduce the risk of errors\. To manually configure your CSV file, the following must be true:
+ UTF\-8 encoding must be explicitly specified, even if its used as a default in most cases\.
+ The first line must contain the column headers: `File`, `Line`, `Begin Offset`, `End Offset`, `Type`\.

We highly recommended that CSV input files are generated programmatically to avoid potential issues\.

The following example uses Python to generate a CSV for the annotations shown above:

```
import csv 
with open("./annotations/annotations.csv", "w", encoding="utf-8") as csv_file:
    csv_writer = csv.writer(csv_file)
    csv_writer.writerow(["File", "Line", "Begin Offset", "End Offset", "Type"])
    csv_writer.writerow(["documents.txt", 0, 0, 11, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 1, 0, 5, "ENGINEER"])
    csv_writer.writerow(["documents.txt", 3, 25, 30, "MANAGER"])
```