# ICD\-10\-CM Linking<a name="ontology-linking-icd10"></a>

 Use **InferICD10CM** to detect possible medical conditions as entities and link them to codes from the 2019 version of [ the International Classification of Diseases, 10th Revision, Clinical Modification \(ICD\-10\-CM\)](https://www.cdc.gov/nchs/icd/icd10cm.htm)\. The ICD\-10\-CM is provided by the US Centers for Disease Control \(CDC\)\.

For each detected potential medical condition, Amazon Comprehend Medical lists the matching ICD\-10\-CM codes and descriptions\. They are listed in descending order of confidence along with the confidence scores\. The scores indicate the confidence in the accuracy of the entities matched to the concepts\. Use the ICD\-10\-CM codes for downstream analysis\. Related information such as signs, symptoms, and negation are recognized as traits\. Additional information such as anatomical designations and acuity are listed as attributes\.

**InferICD10CM** is well suited for the following scenarios:
+  Assistance for professional medical coding for patient records\. 
+  Clinical studies and trials\. 
+  Integration with a medical software system\. 
+  Early detection and diagnosis\. 
+  Population health management\. 

## Important Notice<a name="important-notice"></a>

The **InferICD10CM** operation of Amazon Comprehend Medical is not a substitute for professional medical advice, diagnosis, or treatment\. Identify the right confidence threshold for your use case, and use high confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately trained human reviewers\. All operations of Amazon Comprehend Medical should only be used in patient care scenarios after review for accuracy and sound medical judgment by trained medical professionals\.

## ICD\-10\-CM Category<a name="icd10-cm-category"></a>

**InferICD10CM** detects entities in the `MEDICAL_CONDITION` category\. Additional related information is also detected and linked as attributes or traits\.

## ICD\-10\-CM Type<a name="icd10-cm-type"></a>

 **InferICD10CM** detects entities of the type `DX_NAME.` 

## ICD\-10\-CM Traits<a name="icd10-cm-traits"></a>

**InferICD10CM** detects the following contextual information as traits: 
+ `Diagnosis:` An identification of a medical condition that is determined by evaluation of the symptoms\.
+ `Negation:` An indication that a medical condition is not present\.
+ `Sign:` A medical condition that is reported by the physician\.
+ `Symptom:` A medical condition reported by the patient\.

## ICD\-10\-CM Attributes<a name="icd10-cm-attributes"></a>

**InferICD10CM** detects the following contextual information as attributes: 
+ `Direction:` Directional terms\. For example, left, right medial, lateral, upper, lower, posterior, anterior, distal, proximal, contralateral, bilateral, ipsilateral, dorsal, ventral, and so on\.
+ `System, Organ or Site:` anatomical location\.
+ `Acuity:` Determination of disease instance, such as chronic, acute, sudden, persistent, or gradual\. This only applies to the MEDICAL\_CONDITION type\. 

## Input and Response Examples<a name="icd10cminput"></a>

This section shows an example of using the **InferICD10CM** operation\. The following text is an example of the JSON input: 

```
        {
    "Text": "Pt is 40yo mother, highschool teacher HPI : Sleeping trouble on present dosage of Clonidine. Severe Rash  on face and leg, slightly itchy  Meds : Vyvanse 50 mgs po at breakfast daily,             Clonidine 0.2 mgs -- 1 and 1 / 2 tabs po qhs HEENT : Boggy inferior turbinates, No oropharyngeal lesion Lungs : clear Heart : Regular rhythm Skin :  Mild erythematous eruption to hairline Follow-up as scheduled"
}
```

Based on the input above, you will receive the following\. This is an abbreviated example of the output: 

```
[
    {
"Entities": [
        {
            "Category": "MEDICAL_CONDITION",
            "BeginOffset": 44,
            "EndOffset": 60,
            "Text": "Sleeping trouble",
            "ICD10CMConcepts": [
                {
                    "Code": "G47.9",
                    "Score": 0.7833366394042969,
                    "Description": "Sleep disorder, unspecified"
                },
                {
                    "Code": "R40.0",
                    "Score": 0.30980610847473145,
                    "Description": "Somnolence"
                },
                {
                    "Code": "G47.10",
                    "Score": 0.2419784516096115,
                    "Description": "Hypersomnia, unspecified"
                },
                {
                    "Code": "G47.30",
                    "Score": 0.20712727308273315,
                    "Description": "Sleep apnea, unspecified"
                },
                {
                    "Code": "G47.00",
                    "Score": 0.18955594301223755,
                    "Description": "Insomnia, unspecified"
                }
            ],
            "Traits": [
                {
                    "Score": 0.5823034048080444,
                    "Name": "SYMPTOM"
                }
            ],
            "Score": 0.8271645307540894,
            "Attributes": [],
            "Type": "DX_NAME",
            "Id": 0
        },
        {
            "Category": "MEDICAL_CONDITION",
            "BeginOffset": 100,
            "EndOffset": 104,
            "Text": "Rash",
            "ICD10CMConcepts": [
                {
                    "Code": "R21",
                    "Score": 0.7734980583190918,
                    "Description": "Rash and other nonspecific skin eruption"
                },
                {
                    "Code": "L27.0",
                    "Score": 0.104293592274189,
                    "Description": "Generalized skin eruption due to drugs and medicaments taken internally"
                },
                {
                    "Code": "L29.9",
                    "Score": 0.08036035299301147,
                    "Description": "Pruritus, unspecified"
                },
                {
                    "Code": "L53.9",
                    "Score": 0.07569799572229385,
                    "Description": "Erythematous condition, unspecified"
                },
                {
                    "Code": "L74.0",
                    "Score": 0.07291091233491898,
                    "Description": "Miliaria rubra"
                }
            ],
            "Traits": [
                {
                    "Score": 0.6524375081062317,
                    "Name": "SYMPTOM"
                }
            ],
            "Score": 0.9965221881866455,
            "Attributes": [
                {
                    "BeginOffset": 109,
                    "EndOffset": 113,
                    "Text": "face",
                    "Traits": [],
                    "Score": 0.9851959943771362,
                    "Type": "SYSTEM_ORGAN_SITE",
                    "Id": 2,
                    "RelationshipScore": 0.9811109900474548
                },
                {
                    "BeginOffset": 118,
                    "EndOffset": 121,
                    "Text": "leg",
                    "Traits": [],
                    "Score": 0.9941712021827698,
                    "Type": "SYSTEM_ORGAN_SITE",
                    "Id": 3,
                    "RelationshipScore": 0.9926889538764954
                }
            ],
            "Type": "DX_NAME",
            "Id": 1
        },
        {
            "Category": "MEDICAL_CONDITION",
            "BeginOffset": 132,
            "EndOffset": 137,
            "Text": "itchy",
            "ICD10CMConcepts": [
                {
                    "Code": "L29.9",
                    "Score": 0.7146732211112976,
                    "Description": "Pruritus, unspecified"
                },
                {
                    "Code": "R21",
                    "Score": 0.15261031687259674,
                    "Description": "Rash and other nonspecific skin eruption"
                },
                {
                    "Code": "L29",
                    "Score": 0.13776351511478424,
                    "Description": "Pruritus"
                },
                {
                    "Code": "L29.0",
                    "Score": 0.10539321601390839,
                    "Description": "Pruritus ani"
                },
                {
                    "Code": "H04.203",
                    "Score": 0.08991283923387527,
                    "Description": "Unspecified epiphora, bilateral"
                }
            ],
            "Traits": [],
            "Score": 0.5751778483390808,
            "Attributes": [
                {
                    "BeginOffset": 109,
                    "EndOffset": 113,
                    "Text": "face",
                    "Traits": [],
                    "Score": 0.9851959943771362,
                    "Type": "SYSTEM_ORGAN_SITE",
                    "Id": 2,
                    "RelationshipScore": 0.8954095840454102
                },
                {
                    "BeginOffset": 118,
                    "EndOffset": 121,
                    "Text": "leg",
                    "Traits": [],
                    "Score": 0.9941712021827698,
                    "Type": "SYSTEM_ORGAN_SITE",
                    "Id": 3,
                    "RelationshipScore": 0.9260532259941101
                }
            ],
            "Type": "DX_NAME",
            "Id": 4
        },
        {
            "Category": "MEDICAL_CONDITION",
            "BeginOffset": 249,
            "EndOffset": 274,
            "Text": "Boggy inferior turbinates",
            "ICD10CMConcepts": [
                {
                    "Code": "I51.89",
                    "Score": 0.2947992980480194,
                    "Description": "Other ill-defined heart diseases"
                },
                {
                    "Code": "J34.89",
                    "Score": 0.23306512832641602,
                    "Description": "Other specified disorders of nose and nasal sinuses"
                },
                {
                    "Code": "N85.8",
                    "Score": 0.22112059593200684,
                    "Description": "Other specified noninflammatory disorders of uterus"
                },
                {
                    "Code": "I21.19",
                    "Score": 0.1781269907951355,
                    "Description": "ST elevation (STEMI) myocardial infarction involving other coronary artery of inferior wall"
                },
                {
                    "Code": "R23.8",
                    "Score": 0.11831703782081604,
                    "Description": "Other skin changes"
                }
            ],
            "Traits": [
                {
                    "Score": 0.8751994967460632,
                    "Name": "SIGN"
                }
            ],
            "Score": 0.788222074508667,
            "Attributes": [
                {
                    "BeginOffset": 241,
                    "EndOffset": 246,
                    "Text": "HEENT",
                    "Traits": [],
                    "Score": 0.9693120718002319,
                    "Type": "SYSTEM_ORGAN_SITE",
                    "Id": 5,
                    "RelationshipScore": 0.9835799336433411
                }
            ],
        },
  
    "ModelVersion": "0.0.0"
```