# Detect Entities Version 2<a name="extracted-med-info-V2"></a>

Use the [DetectEntitiesV2](API_medical_DetectEntitiesV2.md) or [StartEntitiesDetectionV2Job](API_medical_StartEntitiesDetectionV2Job.md) operation to detect the medical entities in your text\. It detects entities in the following categories:
+ `ANATOMY`
+ `MEDICAL_CONDITION`
+ `MEDICATION`
+ `PROTECTED_HEALTH_INFORMATION`
+ `TEST_TREATMENT_PROCEDURE`
+ `TIME_EXPRESSION`

All six categories are detected by the `DetectEntitiesV2` operation\. The [DetectPHI](API_medical_DetectPHI.md) and [StartPHIDetectionJob](API_medical_StartPHIDetectionJob.md) operations detect entities only in the `PROTECTED_HEALTH_INFORMATION` category\. Use them when only protected health information\(PHI\) is required\.

**Important**  
Amazon Comprehend Medical provides confidence scores that indicate the level of confidence in the accuracy of detected entities\. When you are identifying protected health information \(PHI\), evaluate these scores and identify the right confidence threshold for your use case\. Use high\-confidence thresholds in situations that require high accuracy\. For certain use cases, results should be reviewed and verified by appropriately trained human reviewers\. Use Amazon Comprehend Medical in patient care scenarios only after review for accuracy and exercising medical judgment by trained medical professionals\.

 Amazon Comprehend Medical detects information in the following classes:
+ *Entity:* A text reference to the name of relevant objects, such as people, treatments, medications, and medical conditions\. For example, ibuprofen\. 
+ *Category:* The generalized grouping to which an entity belongs\. For example, ibuprofen is part of the `MEDICATION` category\.
+ *Type:* The type of entity detected within a single category\. For example, ibuprofen is in the `GENERIC_NAME` type in the `MEDICATION` category\.
+ *Attribute:* Information related to an entity, such as the dosage of a medication\. For example, 200 mg is an attribute of the ibuprofen entity\.
+ *Trait:* Something that Amazon Comprehend Medical understands about an entity, based on context\. For example, a medication has the `NEGATION` trait if a patient is not taking it\.
+ *Relationship Type:* The relationship between an entity and an attribute\.

Amazon Comprehend Medical provides the location of an entity in the input text\. In the Amazon Comprehend console, it shows the location graphically\. When you use the API, it shows the location by numerical offset\.

Each entity and attribute includes a score that indicates the confidence level that Amazon Comprehend Medical has in the accuracy of the detection\. Each attribute also has a relationship score\. The score indicates the confidence level that Amazon Comprehend Medical has in the accuracy of the relationship between the attribute and its parent entity\. Identify the right confidence threshold for your use case\. Use high\-confidence thresholds in situations that require great accuracy\. Filter out data that doesn't meet the threshold\.

## Anatomy Category<a name="anatomy-v2"></a>

The `ANATOMY` category detects references to the parts of the body or body systems and the locations of those parts or systems\. The category has one entity type\.

### Types<a name="anatomy-type-v2"></a>
+ `SYSTEM_ORGAN_SITE`: Body systems, anatomic locations or regions, and body sites\.

### Attributes<a name="anatomy-attribute-v2"></a>
+ `DIRECTION`: Directional terms\. For example, left, right medial, lateral, upper, lower, posterior, anterior, distal, proximal, contralateral, bilateral, ipsilateral, dorsal, ventral, and so on\.

## Medical Condition Category<a name="medical-condition-v2"></a>

The `MEDICAL_CONDITION` category detects the symptoms and diagnosis of medical conditions\. The category has one entity type, one attribute, and four traits\. One or more traits can be associated with a type\.

### Types<a name="medical-condition-type-v2"></a>
+ `DX_NAME`: All medical conditions listed\. The `DX_NAME` type includes present illness, reason for visit, medical history, review of systems, family history, or patient education\. 

### Attributes<a name="medical-condition-attribute-v2"></a>
+ `ACUITY`: Determination of disease instance, such as chronic, acute, sudden, persistent, or gradual\. 

### Traits<a name="medical-condition-trait-v2"></a>
+ `DIAGNOSIS`: A medical condition that is determined as the cause or result of the symptoms\. Symptoms can be found through physical findings, laboratory or radiological reports, or any other means\. Applies only to the `DX_NAME` type\.
+ `NEGATION`: An indication that a result or action is negative or not being performed\.
+ `SIGN`: A medical condition that the physician reported\. Applies only to the `DX_NAME` type\.
+ `SYMPTOM`: A medical condition reported by the patient\. Applies only to the `DX_NAME` type\.

## Medication Category<a name="medication-v2"></a>

The `MEDICATION` category detects medication and dosage information for the patient\. The category has two entity types, seven attributes, and one trait\. One or more attributes can apply to a type\.

### Types<a name="medication-type-v2"></a>
+ `BRAND_NAME`: The copyrighted brand name of the medication or therapeutic agent\.
+ `GENERIC_NAME`: Non\-brand name, ingredient name, or formula mixture of the medication or therapeutic agent\.

### Attributes<a name="medication-attribute-v2"></a>
+ `DOSAGE`: The amount of medication ordered\.
+ `DURATION`: How long the medication should be administered\.
+ `FORM`: The form of the medication\.
+ `FREQUENCY`: How often to administer the medication\. 
+ `RATE`: Primarily for medication infusions or IVs, the administration rate of the medication\.
+ `ROUTE_OR_MODE`: The administration method of a medication\.
+ `STRENGTH`: The medication strength\.

### Traits<a name="medication-trait-v2"></a>
+ `NEGATION`: Any indication that the patient is not taking a medication\.

## Protected Health Information Category<a name="protected-health-information-v2"></a>

The `PROTECTED_HEALTH_INFORMATION` category detects the patient's personal information\. The category has eight entity types\. See [Detect PHI ](how-medical-phi.md) to learn more about this operation\.

### Types<a name="protected-health-information-types-v2"></a>
+ `ADDRESS`: All geographical subdivisions of an address of any facility, named medical facilities, or wards within a facility\.
+ `AGE`: All components of age, spans of age, or any age mentioned\. This includes those of a patient, family members, or others\. The default is in years unless otherwise noted\.
+ `EMAIL`: Any email address\.
+ `ID`: Social security number, medical record number, facility identification number, clinical trial number, certificate or license number, vehicle or device number\. This includes any biometric number of the patient, place of care, or provider\.
+ `NAME`: All names\. Typically, names of the patient, family, or provider\.
+ `PHONE_OR_FAX`: Any phone, fax, or pager number\. Excludes named phone numbers, such as 1\-800\-QUIT\-NOW and 911\.
+ `PROFESSION`: Any profession or employer that pertains to the patient or the patient's family\. It does include the profession of the clinician mentioned in the note\. 

## Test Treatment Procedure Category<a name="test-treatment-procedure-v2"></a>

The `TEST_TREATMENT_PROCEDURE` category detects the procedures that are used to determine a medical condition\. The category contains three entity types and two attributes\. One or more attributes can be related to an entity of the `TEST_NAME` type\.

### Types<a name="test-treatment-procedure-types-v2"></a>
+ `PROCEDURE_NAME`: Interventions as a one\-time action performed on the patient to treat a medical condition or to provide patient care\.
+ `TEST_NAME`: Procedures performed on a patient for diagnostic, measurement, screening, or rating that might have a resulting value\. This includes any procedure, process, evaluation, or rating to determine a diagnosis, to rule out or find a condition, or to scale or score a patient\.
+ `TREATMENT_NAME`: Interventions performed over a span of time for combating a disease or disorder\. This includes groupings of medications, such as antivirals and vaccinations\.

### Attributes<a name="test-treatment-procedure-attributes-v2"></a>
+ `TEST_VALUE`: The result of a test\. Applies only to the `TEST_NAME` entity type\.
+ `TEST_UNIT`: The unit of measure that might accompany the value of the test\. Applies only to the `TEST_NAME` entity type\.

## Time Expression Category<a name="time-expression-v2"></a>

The `TIME_EXPRESSION` category recognizes entities related to time\. This includes entities such as dates and time expressions such as "three days ago," "today," "currently," "day of admission," "last month," or "16 days\." Results in this category are only returned if they are associated with an entity\. For instance, "Yesterday, the patient took 200 mg of ibuprofen" would return Yesterday as a `TIME_EXPRESSION` entity that overlaps with `GENERIC_NAME` entity "ibuprofen\." However, it would not be recognized as entity in "yesterday, the patient walked their dog\." There are five different types with the Time Expression category, each of which is specific to the `TIME_EXPRESSION` entity type\.

### Types<a name="time-expression-v2-categories"></a>
+ `TIME_TO_MEDICATION_NAME`: The date a medication was taken\. The attributes for this type are `BRAND_NAME` and `GENERIC_NAME`\.
+ `TIME_TO_DX_NAME`: The date a medical condition occurred\. The attribute for this type is `DX_NAME`\. 
+ `TIME_TO_TEST_NAME`: The date a test was performed\. The attribute for this type is `TEST_NAME`\.
+ `TIME_TO_PROCEDURE_NAME`: The date a procedure was performed\. The attribute for this type is `PROCEDURE_NAME`\.
+ `TIME_TO_TREATMENT_NAME`: The date a treatment was administered\. The attribute for this type is `TREATMENT_NAME`\.

### Relationship Type<a name="time-expression-v2-relationship-type"></a>
+  The relationship between an entity and an attribute\. The recognized `Relationship_type` is: 

  `Overlap` – The `TIME_EXPRESSION` concurs with the entity detected\.