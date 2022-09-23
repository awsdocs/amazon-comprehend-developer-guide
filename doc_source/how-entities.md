# Entities<a name="how-entities"></a>

An *entity* is a textual reference to the unique name of a real\-world object such as people, places, and commercial items, and to precise references to measures such as dates and quantities\.

For example, in the text "John moved to 1313 Mockingbird Lane in 2012," "John" might be recognized as a `PERSON`, "1313 Mockingbird Lane" might be recognized as a `LOCATION`, and "2012" might be recognized as a `DATE`\.

Each entity also has a score that indicates the level of confidence that Amazon Comprehend has that it correctly detected the entity type\. You can filter out the entities with lower scores to reduce the risk of using incorrect detections\.

The following table lists the entity types\. 


| Type | Description | 
| --- | --- | 
|  COMMERCIAL\_ITEM  | A branded product | 
|  DATE  | A full date \(for example, 11/25/2017\), day \(Tuesday\), month \(May\), or time \(8:30 a\.m\.\) | 
|  EVENT  | An event, such as a festival, concert, election, etc\. | 
|  LOCATION  | A specific location, such as a country, city, lake, building, etc\. | 
|  ORGANIZATION  | Large organizations, such as a government, company, religion, sports team, etc\. | 
|  OTHER  | Entities that don't fit into any of the other entity categories | 
|  PERSON  | Individuals, groups of people, nicknames, fictional characters | 
|  QUANTITY  | A quantified amount, such as currency, percentages, numbers, bytes, etc\. | 
|  TITLE  | An official name given to any creation or creative work, such as movies, books, songs, etc\. | 

Detect entities operations can be performed using any of the primary languages supported by Amazon Comprehend\. This includes only predefined \(non\-custom\) entity detection\. All documents must be in the same language\.

You can use any of the following API operations to detect entities in a document or set of documents\.
+ [DetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_DetectEntities.html)
+  [BatchDetectEntities](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_BatchDetectEntities.html)
+  [StartEntitiesDetectionJob](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_StartEntitiesDetectionJob.html)

The operations return a list of [API Entity](https://docs.aws.amazon.com/comprehend/latest/APIReference/API_Entity.html) objects, one for each entity in the document\. The `BatchDetectEntities` operation returns a list of `Entity` objects, one list for each document in the batch\. The `StartEntitiesDetectionJob` operation starts an asynchronous job that produces a file containing a list of `Entity` objects for each document in the job\.

The following example is the response from the `DetectEntities` operation\.

```
{
    "Entities": [
        {
            "Text": "today",
            "Score": 0.97,
            "Type": "DATE",
            "BeginOffset": 14,
            "EndOffset": 19
        },
        {
            "Text": "Seattle",
            "Score": 0.95,
            "Type": "LOCATION",
            "BeginOffset": 23,
            "EndOffset": 30
        }
    ],
    "LanguageCode": "en"
}
```