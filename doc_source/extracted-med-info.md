# Detect Entities<a name="extracted-med-info"></a>

**Note**  
This version of the `DetectEntities` operation should not be used for new applications\. You should use version 2 of the operation instead\. All new iterations and enhancements of features will be specific to Detect Entities Version 2\. For more information, see [Detect Entities Version 2](extracted-med-info-V2.md)\.

Use the [DetectEntities](API_medical_DetectEntities.md) operation to detect the medical entities in your text\. It detects entities in the following categories:
+ `ANATOMY`
+ `MEDICAL_CONDITION`
+ `MEDICATION`
+ `PROTECTED_HEALTH_INFORMATION`
+ `TEST_TREATMENT_PROCEDURE`

All five categories are detected by the `DetectEntities` operation\. The [DetectPHI](API_medical_DetectPHI.md) operation detects entities only in the `PROTECTED_HEALTH_INFORMATION` category\. Use it when only PHI \(protected health information\) is required\. For information about this operation, see [Detect PHI ](how-medical-phi.md)\. 

**Important**  
Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of detected entities\. When you are identifying protected health information \(PHI\), evaluate these scores and identify the right confidence threshold for your use case\. Use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately trained human reviewers\. Results from Amazon Comprehend Medical in patient care scenarios should only be used after review by trained medical professionals reviewing results for accuracy and sound medical judgment\.

 Amazon Comprehend Medical detects information in the following classes:
+ *Entity:* A textual reference to the name of relevant objects, such as people, treatments, medications, and medical conditions\. For example, "Ibuprofen\." 
+ *Category:* The generalized grouping to which a detected entity belongs\. For example, "Ibuprofen" is part of the `MEDICATION` category\.
+ *Type:* The type of entity detected, scoped to a category\. For example, "Ibuprofen" is in the `GENERIC_NAME` type in the `MEDICATION` category\.
+ *Attribute:* Information related to a detected entity, such as the dosage of a medication\. For example, "200 mg" is an attribute of the "Ibuprofen" entity\.
+ *Trait:* Something that Amazon Comprehend Medical understands about an entity, based on context\. For example, a medication has the `NEGATION` trait if a patient is not taking it\.

Amazon Comprehend Medical provides the location of an entity in the input text\. In the Amazon Comprehend console, it shows the location graphically\. When you use the API, it shows the location by numerical offset\.

Each entity and attribute includes a score that indicates the level of confidence that Amazon Comprehend Medical has in the accuracy of the detection\. Each attribute also has a relationship score\. This score indicates the level of confidence Amazon Comprehend Medical has in the accuracy of the relationship between the attribute and its parent entity\. Identify the right confidence threshold for your use case\. Use high confidence thresholds in situations that require great accuracy, and filter out data that doesn't meet the threshold\.

## ANATOMY Category<a name="anatomy"></a>

The `ANATOMY` category detects references to the parts of the body or body systems and the locations of those parts or systems\. It contains two entity types\.

### Types<a name="anatomy-type"></a>
+ `DIRECTION`: Directional terms\. For example, left, right medial, lateral, upper, lower, posterior, anterior, distal, proximal, contralateral, bilateral, ipsilateral, dorsal, ventral, and so on\.
+ `SYSTEM_ORGAN_SITE`: Body systems, anatomic locations or regions, and body sites\.

### Example<a name="anatomy-example"></a>

The text "Patient's left lung" returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/left_lung.png)
+ "left" is a `DIRECTION` *type*\.
+ "lung" is a `SYSTEM_ORGAN_SITE` *type*\.

The [DetectEntities](API_medical_DetectEntities.md) operation returns the following JSON structure:

```
{
    "Entities": [
        {
            "Id": 0,
            "BeginOffset": 10,
            "EndOffset": 14,
            "Score": 0.9876197576522827,
            "Text": "left",
            "Category": "ANATOMY",
            "Type": "DIRECTION",
            "Traits": []
        },
        {
            "Id": 1,
            "BeginOffset": 15,
            "EndOffset": 19,
            "Score": 0.9820258021354675,
            "Text": "lung",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        }
    ],
    "UnmappedAttributes": []
}
```

## MEDICAL\_CONDITION Category<a name="medical-condition"></a>

The `MEDICAL_CONDITION` category detects the symptoms and diagnosis of medical conditions\. It contains two entity types and four traits\. One or more traits can be associated with a type\.

### Types<a name="medical-condition-type"></a>
+ `ACUITY`: Determination of disease instance, such as chronic, acute, sudden, persistent, or gradual\. 
+ `DX_NAME`: All medical conditions listed\. The `DX_NAME` type includes present illness, reason for visit, medical history, review of systems, family history, or patient education\. 

### Traits<a name="medical-condition-trait"></a>
+ `DIAGNOSIS`: An identification of a medical condition that is determined by evalutation of the symptoms\. This evaluation comes from physical findings, laboratory or radiological reports, or the patient narrative\. Applies only to the `DX_NAME` type\.
+ `NEGATION`: An indication that a result or action is negative or not being performed\.
+ `SIGN`: A medical condition that the physician reported\. Applies only to the `DX_NAME` type\.
+ `SYMPTOM`: A medical condition reported by the patient\. Applies only to the `DX_NAME` type\.

### Example<a name="medical-condition-example"></a>

The text "Patient is suffering from chronic aching pain 4/10" returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/chronic_pain.png)
+ "aching pain" is the `DX_NAME` *type*\.
+ `SYMPTOM` is a *trait* of the "aching pain" *type*\.
+ "chronic" is the `ACUITY` *type*\.

The [DetectEntities](API_medical_DetectEntities.md) operation returns the following JSON structure:

```
{
    "Entities": [
        {
            "Id": 0,
            "BeginOffset": 26,
            "EndOffset": 33,
            "Score": 0.9961825013160706,
            "Text": "chronic",
            "Category": "MEDICAL_CONDITION",
            "Type": "ACUITY",
            "Traits": []
        },
        {
            "Id": 1,
            "BeginOffset": 34,
            "EndOffset": 45,
            "Score": 0.8380221724510193,
            "Text": "aching pain",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SYMPTOM",
                    "Score": 0.6004688739776611
                }
            ]
        }
    ],
    "UnmappedAttributes": []
}
```

## MEDICATION Category<a name="medication"></a>

The `MEDICATION` category detects medication and dosage information for the patient\. It contains two entity types, seven attributes, and one trait\. One or more attributes can apply to a type\.

### Types<a name="medication-type"></a>
+ `BRAND_NAME`: The copyrighted brand name of the medication or therapeutic agent\.
+ `GENERIC_NAME`: Non\-brand name, ingredient name, or formula mixture of the medication or therapeutic agent\.

### Attributes<a name="medication-attribute"></a>
+ `DOSAGE`: The amount of medication ordered\.
+ `DURATION`: How long the medication should be administered\.
+ `FORM`: The form of the medication\.
+ `FREQUENCY`: How often to administer the medication\. 
+ `RATE`: Primarily for medication infusions or IVs, the administration rate of the medication\.
+ `ROUTE_OR_MODE`: The administration method of a medication\.
+ `STRENGTH`: The medication strength\.

### Traits<a name="medication-trait"></a>
+ `NEGATION`: Any indication that the patient is not taking a medication\.

### Example<a name="medication-example"></a>

The text "Infuse Sodium Chloride 0\.9% solution 1000 mL intravenously daily Rate \- 200 mL/hr for next 3 days" returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/sodiumchloride.png)
+ "Infuse" as a "ROUTE\_OR\_MODE" *attribute* related to the "Sodium Chloride" *type*\.
+ "Sodium Chloride" as a `GENERIC_NAME` *type*\.
+ "0\.9%" as a `STRENGTH` *attribute* related to the "Sodium Chloride" *type*\.
+ "solution" as a `FORM` *attribute* related to the "Sodium Chloride" *type*\.
+ "100 mL as a `DOSAGE` *attribute* related to the "Sodium Chloride" *type*\.
+ "intravenously" as a `ROUTE_OR_MODE` *attribute* related to the "Sodium Chloride" *type*\.
+ "daily" as a `FREQUENCY` *attribute* related to the "Sodium Chloride" *type*\.
+ "200 ml/hr" as a `RATE` *attribute* related to the "Sodium Chloride" *type*\.
+ "next 3 days" as a `DURATION` *attribute* related to the "Sodium Chloride" *type*\.

The [DetectEntities](API_medical_DetectEntities.md) operation returns the following JSON structure:

```
{
    "Entities": [
        {
            "Id": 1,
            "BeginOffset": 7,
            "EndOffset": 22,
            "Score": 0.9998517036437988,
            "Text": "Sodium Chloride",
            "Category": "MEDICATION",
            "Type": "GENERIC_NAME",
            "Traits": [],
            "Attributes": [
                {
                    "Type": "ROUTE_OR_MODE",
                    "Score": 0.32359644770622253,
                    "RelationshipScore": 0.9719992280006409,
                    "Id": 0,
                    "BeginOffset": 0,
                    "EndOffset": 6,
                    "Text": "Infuse",
                    "Traits": []
                },
                {
                    "Type": "STRENGTH",
                    "Score": 0.9976715445518494,
                    "RelationshipScore": 0.7892051339149475,
                    "Id": 2,
                    "BeginOffset": 23,
                    "EndOffset": 27,
                    "Text": "0.9%",
                    "Traits": []
                },
                {
                    "Type": "FORM",
                    "Score": 0.9930835962295532,
                    "RelationshipScore": 0.9956902861595154,
                    "Id": 3,
                    "BeginOffset": 28,
                    "EndOffset": 36,
                    "Text": "solution",
                    "Traits": []
                },
                {
                    "Type": "ROUTE_OR_MODE",
                    "Score": 0.9990690350532532,
                    "RelationshipScore": 0.9801701903343201,
                    "Id": 5,
                    "BeginOffset": 45,
                    "EndOffset": 58,
                    "Text": "intravenously",
                    "Traits": []
                },
                {
                    "Type": "FREQUENCY",
                    "Score": 0.9539222121238708,
                    "RelationshipScore": 0.9864235520362854,
                    "Id": 6,
                    "BeginOffset": 59,
                    "EndOffset": 64,
                    "Text": "daily",
                    "Traits": []
                },
                {
                    "Type": "DURATION",
                    "Score": 0.9392423033714294,
                    "RelationshipScore": 0.9961885809898376,
                    "Id": 8,
                    "BeginOffset": 91,
                    "EndOffset": 97,
                    "Text": "3 days",
                    "Traits": []
                }
            ]
        }
    ],
    "UnmappedAttributes": [
        {
            "Type": "MEDICATION",
            "Attribute": {
                "Type": "DOSAGE",
                "Score": 0.9922149777412415,
                "Id": 4,
                "BeginOffset": 37,
                "EndOffset": 44,
                "Text": "1000 mL",
                "Traits": []
            }
        },
        {
            "Type": "MEDICATION",
            "Attribute": {
                "Type": "RATE",
                "Score": 0.9728594422340393,
                "Id": 7,
                "BeginOffset": 72,
                "EndOffset": 81,
                "Text": "200 mL/hr",
                "Traits": []
            }
        }
    ]
}
```

## PROTECTED\_HEALTH\_INFORMATION Category<a name="protected-health-information"></a>

The `PROTECTED_HEALTH_INFORMATION` category detects the patient's personal information\. It contains eight entity types\. For complete information about the `PROTECTED_HEALTH_INFORMATION` category and how it is detected, see [Detect PHI ](how-medical-phi.md)\.

### Types<a name="protected-health-information-types"></a>
+ `ADDRESS`: All geographical subdivisions of an address of any facility, named medical facilities, or wards within a facility\.
+ `AGE`: All components of age, spans of age, or any age mentioned in the clinical note of a patient or others\. The default is in years unless otherwise noted\.
+ `EMAIL`: Any email address\.
+ `ID`: Any and all identification numbers that are tied to the patient\. This includes patient specific numbers like the Social Security number, medical record number, certificate or license number, vehicle or device number, or any biometric numbers\. It also includes the facility identification number, clinical trial number, place of care, or provider\.

  `DATE`: Any date related to the patient or patient care\. 
+ `ID`: Social security number, medical record number, facility identification number, clinical trial number, certificate or license number, vehicle or device number, any biometric number of the patient, place of care, or provider\.
+ `NAME`: All names mentioned in the clinical note\. Typically, names belonging to the patient, family, or provider\.
+ `PHONE_OR_FAX`: Any phone, fax, or pager number\. Excludes named phone numbers, such as 1\-800\-QUIT\-NOW and 911\.
+ `PROFESSION`: Any profession or employer mentioned in the clinical note that pertains to the patient or the patient's family\. This does not refer to the profession of the clinician mentioned in the note\. 

### Example<a name="protected-health-information-example"></a>

The text "Patient is John Smith, a 48\-year old teacher and resident of Seattle, Washington\." returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/patient.png)
+ "John Smith" is a `NAME` *type*\.
+ "48" is an `AGE` *type*\.
+ "teacher" is a `PROFESSION` *type*\.
+ "Seattle, Washington" is an `ADDRESS` *type*\.

The [DetectEntities](API_medical_DetectEntities.md) operation returns the following JSON structure:

```
{
    "Entities": [
        {
            "Id": 0,
            "BeginOffset": 11,
            "EndOffset": 21,
            "Score": 0.9967977404594421,
            "Text": "John Smith",
            "Category": "PROTECTED_HEALTH_INFORMATION",
            "Type": "NAME",
            "Traits": []
        },
        {
            "Id": 1,
            "BeginOffset": 25,
            "EndOffset": 27,
            "Score": 0.9998422861099243,
            "Text": "48",
            "Category": "PROTECTED_HEALTH_INFORMATION",
            "Type": "AGE",
            "Traits": []
        },
        {
            "Id": 2,
            "BeginOffset": 37,
            "EndOffset": 44,
            "Score": 0.9079490900039673,
            "Text": "teacher",
            "Category": "PROTECTED_HEALTH_INFORMATION",
            "Type": "PROFESSION",
            "Traits": []
        },
        {
            "Id": 3,
            "BeginOffset": 61,
            "EndOffset": 80,
            "Score": 0.986108124256134,
            "Text": "Seattle, Washington",
            "Category": "PROTECTED_HEALTH_INFORMATION",
            "Type": "ADDRESS",
            "Traits": []
        }
    ],
    "UnmappedAttributes": []
}
```

## TEST\_TREATMENT\_PROCEDURE Category<a name="test-treatment-procedure"></a>

The `TEST_TREATMENT_PROCEDURE` category detects the procedures used to determine a medical condition\. It contains three entity types and two attributes\. One or more attributes can be related to an entity of the `TEST_NAME` type\.

### Types<a name="test-treatment-procedure-types"></a>
+ `PROCEDURE_NAME`: Interventions as a one\-time action performed on the patient to treat a medical condition or to provide patient care\.
+ `TEST_NAME`: Procedures performed on a patient for diagnostic, measurement, screening, or rating that might have a resulting value\. This includes any procedure, evaluation, or rating to determine a diagnosis, to rule out a condition, or to scale or score a patient\.
+ `TREATMENT_NAME`: Interventions performed over a span of time for combating a disease or disorder\. This includes groupings of medications, such as antivirals and vaccinations\.

### Attributes<a name="test-treatment-procedure-attributes"></a>
+ `TEST_VALUE`: The result of a test\. Applies only to the `TEST_NAME` entity type\.
+ `TEST_UNIT`: The unit of measure that might accompany the value of the test\. Applies only to the `TEST_NAME` entity type\.

### Example<a name="test-treatment-procedure-example"></a>

The text "Abdominal ultrasound noted acute appendicitis, recommend appendectomy followed by several series of broad spectrum antibiotics" returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/abdominal.png)
+ "Abdominal ultrasound" is a `TEST_NAME` *type*\.
+ "acute" is an `ACUITY` *type*\.
+ "appendicitis" is a `DX_NAME` *type*\.
+ `DIAGNOSIS` is a *trait* of the "appendicitis" *type*\.
+ "appendectomy" is a `PROCEDURE_NAME` *type*\.
+ "broad spectrum antibiotics" is a `TREATMENT_NAME` *type*\.

The [DetectEntities](API_medical_DetectEntities.md) operation returns the following JSON structure:

```
{
    "Entities": [
        {
            "Id": 0,
            "BeginOffset": 0,
            "EndOffset": 20,
            "Score": 0.94855135679245,
            "Text": "Abdominal ultrasound",
            "Category": "TEST_TREATMENT_PROCEDURE",
            "Type": "TEST_NAME",
            "Traits": []
        },
        {
            "Id": 3,
            "BeginOffset": 27,
            "EndOffset": 32,
            "Score": 0.9067845940589905,
            "Text": "acute",
            "Category": "MEDICAL_CONDITION",
            "Type": "ACUITY",
            "Traits": []
        },
        {
            "Id": 4,
            "BeginOffset": 33,
            "EndOffset": 45,
            "Score": 0.9954161643981934,
            "Text": "appendicitis",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "DIAGNOSIS",
                    "Score": 0.9528769254684448
                }
            ]
        },
        {
            "Id": 1,
            "BeginOffset": 57,
            "EndOffset": 69,
            "Score": 0.9957893490791321,
            "Text": "appendectomy",
            "Category": "TEST_TREATMENT_PROCEDURE",
            "Type": "PROCEDURE_NAME",
            "Traits": []
        },
        {
            "Id": 2,
            "BeginOffset": 100,
            "EndOffset": 126,
            "Score": 0.9437107443809509,
            "Text": "broad spectrum antibiotics",
            "Category": "TEST_TREATMENT_PROCEDURE",
            "Type": "TREATMENT_NAME",
            "Traits": []
        }
    ],
    "UnmappedAttributes": []
}
```