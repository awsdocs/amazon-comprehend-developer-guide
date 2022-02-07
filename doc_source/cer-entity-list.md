# Entity lists \(plain text only\)<a name="cer-entity-list"></a>

An entity list for custom entity recognition needs a comma\-separated value \(CSV\) file, with the following columns:
+ **Text**— The text of an entry example exactly as seen in the accompanying document corpus\.
+ **Type**—The customer\-defined entity type\. Entity types must an uppercase, underscore separated string such as MANAGER or SENIOR\_MANAGER\. Up to 25 entity types can be trained per model\. 

The file `documents.txt` contains four lines:

```
Jo Brown is an engineer in the high tech industry.
John Doe has been a engineer for 14 years.
Emilio Johnson is a judge on the Washington Supreme Court.
Our latest new employee, Jane Smith, has been a manager in the industry for 4 years.
```

The CSV file with the list of entities has the following lines: 

```
Text, Type
Jo Brown, ENGINEER
John Doe, ENGINEER
Jane Smith, MANAGER
```

**Note**  
In the entities list, the entry for Emilio Johnson is not present because it does not contain either the ENGINEER or MANAGER entity\. 

A minimum of 200 entity matches are needed per entity in the entity list to train a model for custom entity recognition\.

**Creating your data files**

It is important that your entity list be in a properly configured CSV file so your chance of having problems with your entity list file is minimal\. To manually configure your CSV file, the following must be true:
+ UTF\-8 encoding must be explicitly specified, even if its used as a default in most cases\.
+ It must include the column names: `Type` and `Text`\.

We highly recommended that CSV input files are generated programmatically to avoid potential issues\.

The following example uses Python to generate a CSV for the annotations shown above:

```
import csv 
with open("./entitylist/entitylist.csv", "w", encoding="utf-8") as csv_file:
    csv_writer = csv.writer(csv_file)
    csv_writer.writerow(["Text", "Type"])
    csv_writer.writerow(["Jo Brown", "ENGINEER"])
    csv_writer.writerow(["John Doe", "ENGINEER"])
    csv_writer.writerow(["Jane Smith", "MANAGER"])
```

## Best practices<a name="entitylist-bestresults"></a>

There are a number of things to consider to get the best result when using an entity list, including:
+ The order of the entities in your list has no effects on model training\.
+ Use entity list items that cover 80%\-100% of positive entity examples mentioned in the unannotated corpus of documents\.
+ Avoid entity examples that match non\-entities in the document corpus by removing common words and phrases\. Even a handful of incorrect matches can significantly affect the accuracy of your resulting model\. For example, a word like *the* in the entity list will result in a high number of matches which are unlikely to be the entities you are looking for and thus will significantly affect your accuracy\. 
+ Input data should not contain duplicates\. Presence of duplicate samples might result into test set contamination and therefore negatively affect training process, model metrics, and behavior\.
+ Provide documents that resemble real use cases as closely as possible\. Don't use toy data or synthesized data for production systems\. The input data should be as diverse as possible to avoid overfitting and help underlying model better generalize on real examples\.
+ The entity list is case sensitive, and regular expressions are not currently supported\. However, the trained model can often still recognize entities even if they do not match exactly to the casing provided in the entity list\.
+ If you have an entity that is a substring of another entity \(such as “Smith” and “Jane Smith”\), provide both in the entity list\.

Additional suggestions can be found at [Improving Custom Entity Recognizer Performance](cer-metrics.md#cer-performance) 