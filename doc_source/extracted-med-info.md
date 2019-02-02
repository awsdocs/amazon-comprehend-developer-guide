# Detect Entities<a name="extracted-med-info"></a>

Use the [DetectEntities](API_hera_DetectEntities.md) operation to detect entities in one of the five categories shown in the following table\. All five categories are detected by the **DetectEntities** operation\. The [DetectPHI](API_hera_DetectPHI.md) operation detects entities only in the PHI category, for use cases where only that information is required\. For information about this operation, see [Detect PHI ](how-medical-phi.md)\.

**Important**  
Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of the detected entities\. You should identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately\-trained human reviewers\. For example, Amazon Comprehend Medical should not be used in patient care scenarios without trained medical professionals reviewing results for accuracy and exercising their medical judgment\.

Comprehend Medical detects information using the following classifications:
+ *Entity*: A textual reference to the unique name of a real\-world object such as people, treatments, medications, and medical conditions, and to precise references to measures, such as dates and dosage\. For example, "Ibuprofen\."
+ *Category*: The generalized grouping to which a detected entity belongs, for ease of understanding\. For example, "Ibuprofen" is part of the `MEDICATION` category\.
+ *Type*: The type of entity detected, scoped to a category\. For example, "Ibuprofen" is of the `GENERIC_NAME` type of entity\.
+ *Attribute*: A textual reference to relevant information related to a detected entity, as in dosage is an attribute of a medication\. For example, "200mg" is an attribute of the "Ibuprofen" entity\.
+ *Trait*: Something we understand about an entity, based on context\. For instance, a medication is negated \(`NEGATION` trait\) if a patient is not taking it\.

Comprehend Medical provides the location of the information \(graphically in the console and by numerical offset using the API\)\. 

Each entity and attribute includes a score \(`Score` in the response\) that indicates the level of confidence Amazon Comprehend Medical has in the accuracy of the detection\. Additionally, each attribute has a relationship score \(`RelationshipScore` in the response\) that indicates the level of confidence Amazon Comprehend Medical has in the accuracy of the relationship between the attribute and its parent entity\. You should identify the right confidence threshold for your use case, using high confidence thresholds in situations that require high accuracy, and filter out data that doesn’t meet it\.

## Detected Entities<a name="medical-entities-list"></a>

The following table lists the entities, attributes, types, and traits that can be detected by Comprehend Medical\.


| Category | Name | Description | 
| --- | --- | --- | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  AGE  |  PHI type\. All components of age, spans of age, and any age mentioned, be it patient or family member or others involved in the note\. Default is in years unless otherwise noted\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  NAME  |  PHI type\. All names mentioned in the clinical note, typically belonging to patient, family, or provider\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  PHONE\_OR\_FAX  |  PHI type\. Any phone, fax, pager; excludes named phone numbers such as 1\-800\-QUIT\-NOW as well as 911\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  EMAIL  |  PHI type\. Any email address\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  ID  |  PHI type\. Included is social security number, medical record number, facility identification number, clinical trial number, certificate or license number, vehicle or device number, or biometric number as it pertains to the patient, place of care, or provider\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  URL  |  PHI type\. Any web URL\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  ADDRESS  |  PHI type\. This includes all geographical subdivisions of an address of any facility, named medical facilities, or wards within a facility\.  | 
|  [`PROTECTED_HEALTH_INFORMATION`](#PHI-med-entities)  |  PROFESSION  |  PHI type\. Includes any profession or employer mentioned in a note as it pertains to the patient or the patient’s family, not the profession of the clinician within the note\.  | 
|  [`ANATOMY`](#anatomy)  |  SYSTEM\_ORGAN\_SITE  |  ANATOMY type\. Body systems, anatomic locations or regions, and body sites \(i\.e\., port site\)\.  | 
|  [`ANATOMY`](#anatomy)  |  DIRECTION  |  ANATOMY type\. Directional terms \(i\.e\., left, right, medial, lateral, upper, lower, posterior, anterior, distal, proximal, contralateral, bilateral, ipsilateral, dorsal, ventral, etc\.\)  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  DX\_NAME  |  MEDICAL\_CONDITION type\. All medical conditions listed; includes present illness, reason for visit, past medical history, review of systems, family history, or patient education\. Split into three traits:    SYMPTOM – A medical condition that is patient reported\.    SIGN – A medical condition that physician reported \(anything that was stated as inspected, seen, touched, palpated, percussed, or auscultated\)\.    DIAGNOSIS – A medical condition that has been determined as the cause or results of the symptoms — either via physical findings, laboratory or radiological reports, or any other means — that the patient may or may not have\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  ACUITY  |  MEDICAL\_CONDITION type\. Determination of diseases instance \(i\.e\., chronic, acute, sudden, persistent, gradual\)\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  QUALITY  |  MEDICAL\_CONDITION trait\. Any description of the medical condition or a point in time when it occurred\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  QUANTITY  |  MEDICAL\_CONDITION trait\. Any number description or numeric representation of the medical condition\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  DIAGNOSIS  |  MEDICAL\_CONDITION trait\. Any identification of the nature of an illness\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  SIGN  |  MEDICAL\_CONDITION trait\. Any description or indication that might lead to a diagnosis\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  SYMPTOM  |  MEDICAL\_CONDITION trait\. Any indicator of a specific medical condition\.  | 
|  [`MEDICAL_CONDITION`](#medical-condition)  |  NEGATION  |  MEDICAL\_CONDITION trait\. An indication that a result or action is negative or not being performed\.  | 
|  [`MEDICATION`](#medication)  |  GENERIC\_NAME  |  MEDICATION type\. Non\-brand name, ingredient name, or formula mixture of the medication or therapeutic agent\.  | 
|  [`MEDICATION`](#medication)  |  BRAND\_NAME  |  MEDICATION type\. The copyrighted brand name of the medication or therapeutic agent\.  | 
|  [`MEDICATION`](#medication)  |  STRENGTH  |  MEDICATION attribute\. The medication strength\.  | 
|  [`MEDICATION`](#medication)  |  DOSAGE  |  MEDICATION attribute\. The amount of medication ordered\.  | 
|  [`MEDICATION`](#medication)  |  FORM  |  MEDICATION attribute\. Describes how the medication exists\.  | 
|  [`MEDICATION`](#medication)  |  ROUTE\_OR\_MODE  |  MEDICATION attribute\. The administration method of a medication\.  | 
|  [`MEDICATION`](#medication)  |  FREQUENCY  |  MEDICATION attribute\. Describes how often to administer the medication or treatment\. Describes how often to administer the medication or treatment\.  | 
|  [`MEDICATION`](#medication)  |  DURATION  |  MEDICATION attribute\. Indicates how long the medication should be administered\.  | 
|  [`MEDICATION`](#medication)  |  RATE  |  MEDICATION attribute\. Mainly dealing with medication infusions/IVs, this is the administration rate of the medication\.  | 
|  [`MEDICATION`](#medication)  |  NEGATION  |  MEDICATION trait\. Any indication that the patient is not taking their medication as prescribed\.  | 
|  [`TEST_TREATMENT_PROCEDURE`](#ttp)  |  TEST\_NAME  |  TEST\_TREATMENT\_PROCEDURE type\. Theses are procedures performed for diagnostic, measurement, screening, or rating performed on a patient that may have a resulting value\. This includes any procedure, process, evaluation, or rating for diagnosis determination, to rule out or find a condition, or to scale or score a patient\.  | 
|  [`TEST_TREATMENT_PROCEDURE`](#ttp)  |  PROCEDURE\_NAME  |  TEST\_TREATMENT\_PROCEDURE type\. Interventions as a one\-time action performed on the patient to treat a medical condition or to provide patient care\.  | 
|  [`TEST_TREATMENT_PROCEDURE`](#ttp)  |  TREATMENT\_NAME  |  TEST\_TREATMENT\_PROCEDURE type\. Interventions performed for combating a disease or disorder that is over a series or a span of time; includes grouping of medications \(i\.e\., antivirals\) and vaccinations\.  | 
|  [`TEST_TREATMENT_PROCEDURE`](#ttp)  |  TEST\_VALUE  |  TEST\_TREATMENT\_PROCEDURE attribute\. The result of a test\.  | 
|  [`TEST_TREATMENT_PROCEDURE`](#ttp)  |  TEST\_UNIT  |  TEST\_TREATMENT\_PROCEDURE attribute\. The unit of measure that may accompany the value of the exam\.  | 

## `PROTECTED_HEALTH_INFORMATION`<a name="PHI-med-entities"></a>

Comprehend Medical detects the following:
+ *entities* of type `AGE`, `NAME`, `PHONE_OR_FAX`, `EMAIL`, `ID`, `URL`, `ADDRESS`, and `PROFESSION`\.

For full information on `PROTECTED_HEALTH_INFORMATION` and how they are detected, see [Detect PHI ](how-medical-phi.md)\.

## `MEDICATION`<a name="medication"></a>

Comprehend Medical detects the following:
+ *entities* of type `GENERIC_NAME` or `BRAND_NAME`\.
+ *attributes* related to each medication *entity*, including `DOSAGE`, `FORM`, `ROUTE_OR_MODE`, `FREQUENCY`, `DURATION`, `STRENGTH`, and `RATE`\.
+ A *trait* describing whether the medication was not taken \(`NEGATION`\)\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/sodiumchloride.png)

For example, the text "Infuse Sodium Chloride 0\.9 % solution 1000 mL Intravenously daily Rate = 200 mL/hr for next 3 days" returns:
+ "Sodium Chloride" as `GENERIC_NAME` *entity*
+ "0\.9%" as a `STRENGTH` *attribute* related to the "Sodium Chloride" *entity*
+ "solution" as a `FORM` *attribute* related to the "Sodium Chloride" *entity*
+ "1000mL" as a `DOSAGE` *attribute* related to the "Sodium Chloride" *entity*
+ "intravenously" as a `ROUTE_OR_MODE` *attribute* related to the "Sodium Chloride" *entity*
+ "200 mL/hr" as a `RATE` *attribute* related to the "Sodium Chloride" *entity*
+ "daily" as a `FREQUENCY` *attribute* related to the "Sodium Chloride" *entity*
+ "next 3 days" as a `DURATION` *attribute* related to the "Sodium Chloride" *entity*

## `MEDICAL_CONDITION`<a name="medical-condition"></a>

Comprehend Medical detects the following:
+ *entities* of type `DX_NAME` or `ACUITY`\.
+ A *trait* describing whether the medical condition entity is a `DIAGNOSIS`, `SIGN` \(observed by practitioner\), or `SYMPTOM` \(observed by patient\)\.
+ A *trait* describing whether the medical condition entity is not present in the patient \(`NEGATION`\)\.

For example, the text "Patient is suffering from chronic aching pain 4/10" returns:

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/chronic_pain.png)
+ "aching pain" as `DX_NAME` *entity*
+ `SYMPTOM` as a *trait* of the "aching pain" *entity*
+ "chronic" as `ACUITY` *entity*

## `TEST_TREATMENT_PROCEDURE`<a name="ttp"></a>

Comprehend Medical detects the following:
+ *entities* of type `TEST_NAME`, `TREATMENT_NAME`, or `PROCEDURE_NAME`\.
+ *attributes* related to each TTP entity, including `TEST_VALUE` and `TEST_UNIT`\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/bloodpressure.png)

For example, the text "Patient has a blood pressure of 120/80" returns:
+ "blood pressure" as `TEST_NAME` *entity*
+ "120/80" as a `TEST_VALUE` *attribute* related to "blood pressure" *entity*

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/abdominal.png)

For example, the text "Abdominal ultrasound noted acute appendicitis, recommend appendectomy followed by several series of broad spectrum antibiotics" returns:
+ "Abdominal ultrasound" as a `TEST_NAME` *entity*
+ "acute appendicitis" as a `TEST_VALUE` *attribute* related to the `TEST_NAME` entity
+ "appendectomy" as a `PROCEDURE_NAME` *entity*
+ "broad spectrum antibiotics" as a `TREATMENT_NAME` *entity*

## `ANATOMY`<a name="anatomy"></a>

Comprehend Medical detects the following:
+ *entities* of type `SYSTEM_ORGAN_SITE` \(for example, lung\) or `DIRECTION` \(for example left\)\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/left_lung.png)

For example, the text "Patient’s left lung" returns:
+ "left" as `DIRECTION` *entity*
+ "lung" as `SYSTEM_ORGAN_SITE` *entity*

## Example<a name="HEENT_example"></a>

In the text "MEDS : Vyvanse 50 mgs po at breakfast daily HEENT: Oropharynx clear\. Sclerae are anicteric\. EXTREMITIES: No clubbing, cyanosis, left lower extremity present with edema", the Comprehend Medical analysis would include "HEENT" recognized as an anatomical entity of type `SYSTEM_ORGAN_SITE` and would recognize "Sclerae are anicteric" as both a medical condition entity of type `DX_NAME` and a `SIGN` trait of that condition\.

When using the Comprehend Medical console, this text would be analyzed in this way: 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/comprehend/latest/dg/images/gs-cm-image-5.png)

In JSON, Comprehend Medical would provide the following response: 

```
{
    "Entities": [
        {
            "Id": 0,
            "BeginOffset": 7,
            "EndOffset": 14,
            "Score": 0.99925297498703,
            "Text": "Vyvanse",
            "Category": "MEDICATION",
            "Type": "BRAND_NAME",
            "Traits": [],
            "Attributes": [
                {
                    "Type": "DOSAGE",
                    "Score": 0.9753520488739014,
                    "RelationshipScore": 0.999964714050293,
                    "Id": 1,
                    "BeginOffset": 15,
                    "EndOffset": 21,
                    "Text": "50 mgs",
                    "Traits": []
                },
                {
                    "Type": "ROUTE_OR_MODE",
                    "Score": 0.997583270072937,
                    "RelationshipScore": 0.9990845918655396,
                    "Id": 2,
                    "BeginOffset": 22,
                    "EndOffset": 24,
                    "Text": "po",
                    "Traits": []
                },
                {
                    "Type": "FREQUENCY",
                    "Score": 0.9308977127075195,
                    "RelationshipScore": 0.9998767375946045,
                    "Id": 3,
                    "BeginOffset": 25,
                    "EndOffset": 43,
                    "Text": "at breakfast daily",
                    "Traits": []
                }
            ]
        },
        {
            "Id": 9,
            "BeginOffset": 44,
            "EndOffset": 49,
            "Score": 0.9810491800308228,
            "Text": "HEENT",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        },
        {
            "Id": 10,
            "BeginOffset": 51,
            "EndOffset": 61,
            "Score": 0.9756641387939453,
            "Text": "Oropharynx",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        },
        {
            "Id": 4,
            "BeginOffset": 51,
            "EndOffset": 67,
            "Score": 0.8910155296325684,
            "Text": "Oropharynx clear",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SIGN",
                    "Score": 0.9442662000656128
                }
            ]
        },
        {
            "Id": 11,
            "BeginOffset": 69,
            "EndOffset": 76,
            "Score": 0.9391819834709167,
            "Text": "Sclerae",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        },
        {
            "Id": 5,
            "BeginOffset": 69,
            "EndOffset": 90,
            "Score": 0.8764611482620239,
            "Text": "Sclerae are anicteric",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SIGN",
                    "Score": 0.9571187496185303
                }
            ]
        },
        {
            "Id": 12,
            "BeginOffset": 92,
            "EndOffset": 103,
            "Score": 0.9984232187271118,
            "Text": "EXTREMITIES",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        },
        {
            "Id": 6,
            "BeginOffset": 108,
            "EndOffset": 116,
            "Score": 0.9986805319786072,
            "Text": "clubbing",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SIGN",
                    "Score": 0.9817004799842834
                },
                {
                    "Name": "NEGATION",
                    "Score": 0.9858788847923279
                }
            ]
        },
        {
            "Id": 7,
            "BeginOffset": 118,
            "EndOffset": 126,
            "Score": 0.999649167060852,
            "Text": "cyanosis",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SIGN",
                    "Score": 0.9852961897850037
                },
                {
                    "Name": "NEGATION",
                    "Score": 0.9851279854774475
                }
            ]
        },
        {
            "Id": 13,
            "BeginOffset": 128,
            "EndOffset": 132,
            "Score": 0.9767290353775024,
            "Text": "left",
            "Category": "ANATOMY",
            "Type": "DIRECTION",
            "Traits": []
        },
        {
            "Id": 14,
            "BeginOffset": 133,
            "EndOffset": 138,
            "Score": 0.9425379037857056,
            "Text": "lower",
            "Category": "ANATOMY",
            "Type": "DIRECTION",
            "Traits": []
        },
        {
            "Id": 15,
            "BeginOffset": 140,
            "EndOffset": 149,
            "Score": 0.9737963676452637,
            "Text": "extremity",
            "Category": "ANATOMY",
            "Type": "SYSTEM_ORGAN_SITE",
            "Traits": []
        },
        {
            "Id": 8,
            "BeginOffset": 163,
            "EndOffset": 168,
            "Score": 0.9868903160095215,
            "Text": "edema",
            "Category": "MEDICAL_CONDITION",
            "Type": "DX_NAME",
            "Traits": [
                {
                    "Name": "SIGN",
                    "Score": 0.9313799142837524
                }
            ]
        }
    ],
    "UnmappedAttributes": []
}
```