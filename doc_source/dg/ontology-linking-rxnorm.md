# RxNorm Linking<a name="ontology-linking-rxnorm"></a>

 Use the **InferRxNorm** operation to identify medications that are listed in a patient record as entities\. The operation also links those entities to concept identifiers \(RxCUI\) from [ the RxNorm database from the National Library of Medicine](https://www.nlm.nih.gov/research/umls/rxnorm/docs/rxnormfiles.html )\. Each RxCUI is unique for different strengths and dose forms\. Amazon Comprehend Medical lists the top potentially matching RxCUIs for each medication that it detects in descending order by confidence score\. Use the RxCUI codes for downstream analysis not possible with unstructured text\. Related information such as strength, frequency, dose, dose form, and route of administration are listed as attributes in JSON format\.

 **InferRxNorm** is well suited for the following scenarios:
+  Screening for medications the patient has taken\. 
+  Preventing potential negative reactions between newly prescribed drugs and drugs the patient is already taking\. 
+  Screening for inclusion in clinical trials based on drug history using the RxCUI\. 
+  Checking whether the dosage and frequency of a drug is appropriate\. 
+  Screening for uses, indications, and side effects of drugs\. 
+  Population health management\. 

## Important Notice<a name="important-notice"></a>

The **InferRxNorm** operation of Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately trained human reviewers\. All operations of Amazon Comprehend Medical should only be used in patient care scenarios after review for accuracy and sound medical judgment by trained medical professionals\.

## RxNorm Category<a name="medication-v2-rxnorm"></a>

**InferRxNorm** detects entities in the `MEDICATION` category\. Additional related information is also detected and linked as attributes or traits\.

## RxNorm Types<a name="medication-type-rxnorm"></a>

 The types of entity within the `Medication` category are:
+ `BRAND_NAME`: The copyrighted brand name of the medication or therapeutic agent\.
+ `GENERIC_NAME`: Non\-brand name, ingredient name, or formula mixture of the medication or therapeutic agent\.

## RxNorm Attributes<a name="medication-attribute-rxnorm"></a>
+ `DOSAGE`: The amount of medication ordered\.
+ `DURATION`: How long the medication should be administered\.
+ `FORM`: The form of the medication\.
+ `FREQUENCY`: How often to administer the medication\. 
+ `RATE`: Primarily for medication infusions or IVs, the administration rate of the medication\.
+ `ROUTE_OR_MODE`: The administration method of a medication\.
+ `STRENGTH`: The medication strength\.

## RxNorm Trait<a name="medication-trait-v2-rxnorm"></a>
+ `NEGATION`: Any indication that the patient is not taking a medication\.

### Input and Response Examples<a name="rxnorminput"></a>

This section shows an example of using the **InferRxNorm** operation\. The following text is an example of the input JSON:

```
{
    "Text": "fluoride topical ( fluoride 1.1 % topical gel ) 1 application 
        Topically daily Brush onto teeth before bed time , spit , do not rinse,
        eat or drink for 20-30 minutes"
}
```

Based on the input above, you will receive the following result:

```
[
    {
        [
    {
        "Id": 0,
        "Text": "fluoride",
        "Category": "MEDICATION",
        "Type": "GENERIC_NAME",
        "Score": 0.8712447285652161,
        "BeginOffset": 15,
        "EndOffset": 23,
        "Attributes": [
            {
                "Type": "ROUTE_OR_MODE",
                "Score": 0.8275620341300964,
                "RelationshipScore": 0.9997424483299255,
                "Id": 1,
                "BeginOffset": 24,
                "EndOffset": 31,
                "Text": "topical",
                "Traits": []
            },
            {
                "Type": "STRENGTH",
                "Score": 0.9978499412536621,
                "RelationshipScore": 0.9971910119056702,
                "Id": 3,
                "BeginOffset": 43,
                "EndOffset": 48,
                "Text": "1.1 %",
                "Traits": []
            },
            {
                "Type": "FORM",
                "Score": 0.9408299326896667,
                "RelationshipScore": 0.9997219443321228,
                "Id": 4,
                "BeginOffset": 49,
                "EndOffset": 60,
                "Text": "topical gel",
                "Traits": []
            },
            {
                "Type": "DOSAGE",
                "Score": 0.9950674772262573,
                "RelationshipScore": 0.9999516010284424,
                "Id": 5,
                "BeginOffset": 63,
                "EndOffset": 76,
                "Text": "1 application",
                "Traits": []
            },
            {
                "Type": "ROUTE_OR_MODE",
                "Score": 0.9967094659805298,
                "RelationshipScore": 0.9985153079032898,
                "Id": 6,
                "BeginOffset": 77,
                "EndOffset": 86,
                "Text": "Topically",
                "Traits": []
            },
            {
                "Type": "FREQUENCY",
                "Score": 0.9728374481201172,
                "RelationshipScore": 0.9999150037765503,
                "Id": 7,
                "BeginOffset": 87,
                "EndOffset": 92,
                "Text": "daily",
                "Traits": []
            }
        ],
        "Traits": [],
        "RxNormConcepts": [
            {
                "ConceptName": "Sodium Fluoride 0.011 MG/MG Oral Gel",
                "ConceptId": "1486566",
                "Score": 0.9764410257339478
            },
            {
                "ConceptName": "Sodium Fluoride 0.011 MG/MG Oral Gel [FluoriSHIELD]",
                "ConceptId": "1546240",
                "Score": 0.8418328762054443
            },
            {
                "ConceptName": "Hydrofluoric Acid 0.01 MG/MG / Phosphoric acid 0.0112 MG/MG / Sodium Fluoride 0.018 MG/MG Oral Gel",
                "ConceptId": "1297381",
                "Score": 0.7141376733779907
            },
            {
                "ConceptName": "Stannous Fluoride 0.014 MG/MG Oral Gel",
                "ConceptId": "701932",
                "Score": 0.49637168645858765
            },
            {
                "ConceptName": "Sodium Fluoride 0.011 MG/MG Oral Gel [Neutracare]",
                "ConceptId": "1596938",
                "Score": 0.478127658367157
            }
        ]
    },
    {
        "Id": 2,
        "Text": "fluoride",
        "Category": "MEDICATION",
        "Type": "GENERIC_NAME",
        "Score": 0.9971680045127869,
        "BeginOffset": 34,
        "EndOffset": 42,
        "Attributes": [],
        "Traits": [],
        "RxNormConcepts": [
            {
                "ConceptName": "Fluorine",
                "ConceptId": "1310123",
                "Score": 0.9384168982505798
            },
            {
                "ConceptName": "Sodium Fluoride",
                "ConceptId": "9873",
                "Score": 0.9174549579620361
            },
            {
                "ConceptName": "magnesium fluoride",
                "ConceptId": "1435860",
                "Score": 0.8124921917915344
            },
            {
                "ConceptName": "Acidulated Phosphate Fluoride",
                "ConceptId": "236",
                "Score": 0.4174852967262268
            },
            {
                "ConceptName": "Sodium Fluoride 0.0025 MG/MG Toothpaste",
                "ConceptId": "1044547",
                "Score": 0.3444318175315857
            }
        ]
    }
]
```

**InferRxNorm** also recognizes negation, as shown in the following input example\. 

```
{
    "Text": "patient no longer taking warfarin"
}
```

Based on the input above, you receive the following result\.

```
[
    {
        "Id": 0,
        "Text": "warfarin",
        "Category": "MEDICATION",
        "Type": "GENERIC_NAME",
        "Score": 0.9997209906578064,
        "BeginOffset": 25,
        "EndOffset": 33,
        "Attributes": [],
        "Traits": [
            {
                "Name": "NEGATION",
                "Score": 0.7574219703674316
            }
        ],
        "RxNormConcepts": [
            {
                "ConceptName": "Warfarin",
                "ConceptId": "11289",
                "Score": 0.9439864158630371
            },
            {
                "ConceptName": "Warfarin Sodium 2 MG Oral Tablet",
                "ConceptId": "855302",
                "Score": 0.5045595169067383
            },
            {
                "ConceptName": "Warfarin Sodium 3 MG Oral Tablet",
                "ConceptId": "855318",
                "Score": 0.4175175130367279
            },
            {
                "ConceptName": "Warfarin Sodium 6 MG Oral Tablet",
                "ConceptId": "855338",
                "Score": 0.3222610652446747
            },
            {
                "ConceptName": "Warfarin Sodium 2.5 MG Oral Tablet [Coumadin]",
                "ConceptId": "855314",
                "Score": 0.1963760107755661
            }
        ]
    }
]
```