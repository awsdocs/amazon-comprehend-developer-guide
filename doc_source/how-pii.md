# Detect Personally Identifiable Information \(PII\)<a name="how-pii"></a>

You can use Amazon Comprehend to detect entities in your text that contain personally identifiable information \(PII\), or *PII entities*\. A PII entity is a textual reference to personal data that could be used to identify an individual, such as an address, bank account number, or phone number\.

For example, you can detect the PII entities in the following text by submitting it to Amazon Comprehend:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

When Amazon Comprehend completes its analysis, it returns output that either locates or redacts the PII entities in the text\.

For example, if you choose to locate the PII entities, the output includes the character offsets for each one, along with the entity type and other details\. In this case, the output states that "Paul Santos" has the type `NAME`, "1111\-0000\-1111\-0000" has the type `CREDIT_DEBIT_NUMBER`, and "123 Any Street, Seattle, WA 98109" has the type `ADDRESS`\.

Alternatively, if you choose to redact the PII entities, Amazon Comprehend returns a copy of the input text in which each PII entity is redacted:

*Hello \*\*\*\*\* \*\*\*\*\*\*\. The latest statement for your credit card account \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* was mailed to \*\*\* \*\*\* \*\*\*\*\*\*\* \*\*\*\*\*\*\*\* \*\* \*\*\*\*\*\.*

You can detect PII entities with both real\-time synchronous operations and batch asynchronous jobs\. However, you must use an asynchronous job if you want to produce output with redacted PII entities\. 

You can use the following operations to detect PII entities in a document or set of documents:
+ [DetectPiiEntities](API_DetectPiiEntities.md)
+ [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md)

You can use the following operation to label PII in a document or set of documents:
+ [ContainsPiiEntities](API_ContainsPiiEntities.md)

## PII Entity Types<a name="how-pii-types"></a>

Amazon Comprehend can detect the following types of PII entities:


| PII entity type | Description | 
| --- | --- | 
| ADDRESS |  A physical address, such as "100 Main Street, Anytown, USA" or "Suite \#12, Building 123"\. An address can include a street, building, location, city, state, country, county, zip, precinct, neighborhood, and more\.  | 
| AGE |  An individual's age, including the quantity and unit of time\. For example, in the phrase "I am 40 years old," Amazon Comprehend recognizes "40 years" as an age\.   | 
| AWS\_ACCESS\_KEY |  A unique identifier that's associated with a secret access key; the access key ID and secret access key are used together to sign programmatic AWS requests cryptographically\.  | 
| AWS\_SECRET\_KEY |  A unique identifier that's associated with an access key; the access key ID and secret access key are used together to sign programmatic AWS requests cryptographically\.  | 
| BANK\_ACCOUNT\_NUMBER |  A US bank account number\. These are typically between 10 \- 12 digits long, but Amazon Comprehend also recognizes bank account numbers when only the last 4 digits are present\.  | 
| BANK\_ROUTING |  A US bank account routing number\. These are typically 9 digits long, but Amazon Comprehend also recognizes routing numbers when only the last 4 digits are present\.  | 
| CREDIT\_DEBIT\_CVV |  A 3\-digit card verification code \(CVV\) that is present on VISA, MasterCard, and Discover credit and debit cards\. In American Express credit or debit cards, it is a 4\-digit numeric code\.  | 
| CREDIT\_DEBIT\_EXPIRY |  The expiration date for a credit or debit card\. This number is usually 4 digits long and formatted as month/year or MM/YY\. For example, Amazon Comprehend can recognize expiration dates such as 01/21, 01/2021, and Jan 2021\.   | 
| CREDIT\_DEBIT\_NUMBER |  The number for a credit or debit card\. These numbers can vary from 13 to 16 digits in length, but Amazon Comprehend also recognizes credit or debit card numbers when only the last 4 digits are present\.   | 
| DATE\_TIME |  A date can include a year, month, day, day of week, or time of day\. For example, Amazon Comprehend recognizes "January 19, 2020" or "11 am" as dates\. Amazon Comprehend will recognize partial dates, date ranges, and date intervals\. It will also recognize decades, such as "the 1990s"\.  | 
| DRIVER\_ID |  The number assigned to a driver's license, which is an official document permitting an individual to operate one or more motorized vehicles on a public road\. A driver's license number consists of alphanumeric characters\.   | 
| EMAIL |  An email address, such as marymajor@email\.com\.  | 
| IP\_ADDRESS |  An IPv4 address, such as 198\.51\.100\.0\.  | 
| MAC\_ADDRESS |  A media access control \(MAC\) address is a unique identifier assigned to a network interface controller \(NIC\)\.   | 
| NAME |  An individual's name\. This entity type does not include titles, such as Mr\., Mrs\., Miss, or Dr\. Amazon Comprehend does not apply this entity type to names that are part of organizations or addresses\. For example, Amazon Comprehend recognizes the "John Doe Organization" as an organization, and it recognizes "Jane Doe Street" as an address\.   | 
| PASSPORT\_NUMBER |  A US passport number\. Passport numbers range from 6 \- 9 alphanumeric characters\.  | 
| PASSWORD |  An alphanumeric string that is used as a password, such as "\*very20special\#pass\*"\.  | 
| PHONE |  A phone number\. This entity type also includes fax and pager numbers\.  | 
| PIN |  A 4\-digit personal identification number \(PIN\) that allows someone to access their bank account information\.  | 
| SSN |  A Social Security Number \(SSN\) is a 9\-digit number that is issued to US citizens, permanent residents, and temporary working residents\. Amazon Comprehend also recognizes Social Security Numbers when only the last 4 digits are present\.  | 
| URL |  A web address, such as www\.example\.com\.  | 
| USERNAME |  A user name that identifies an account, such as a login name, screen name, nick name, or handle\.  | 

## Locate PII Entities<a name="how-pii-locate"></a>

To locate the PII entities in your text, you can quickly analyze a single document, or you can start an asynchronous batch job on a large collection of documents\.

To locate the PII entities in a single document, submit a [DetectPiiEntities](API_DetectPiiEntities.md) request, and include the document text in your request body\. Your input text can include up to 5,000 bytes of UTF\-8 encoded characters\. Amazon Comprehend returns a list that provides the character offsets and other details for each PII entity that it detects, as shown by the following example response:

```
{
    "Entities": [
        {
            "Score": 0.9999669790267944,
            "Type": "NAME",
            "BeginOffset": 6,
            "EndOffset": 18
        },
        {
            "Score": 0.8905550241470337,
            "Type": "CREDIT_DEBIT_NUMBER",
            "BeginOffset": 69,
            "EndOffset": 88
        },
        {
            "Score": 0.9999889731407166,
            "Type": "ADDRESS",
            "BeginOffset": 103,
            "EndOffset": 138
        }
    ]
}
```

In addition to the character offsets, Amazon Comprehend provides the following for each PII entity:
+ A score that estimates the probability that the detected text span is the detected entity type\.
+ The PII entity type\.

To run the same analysis on a large collection of documents, run an asynchronous batch job\. To run the job, upload your documents to Amazon S3, and submit a [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md) request\. In your request, include the following required parameters:
+ `InputDataConfig` – Provide an [InputDataConfig](API_InputDataConfig.md) definition for your request, which includes the input properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location of your input documents\.
+ `OutputDataConfig` – Provide an [OutputDataConfig](API_OutputDataConfig.md) definition for your request, which includes the output properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location where Amazon Comprehend writes the results of its analysis\.
+ `DataAccessRoleArn` – Provide the Amazon Resource Name \(ARN\) of an AWS Identity and Access Management role\. This role must grant Amazon Comprehend read access to your input data and write access to your output location in Amazon S3\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.
+ `Mode` – Set this parameter to `ONLY_OFFSETS`\. With this setting, the output provides the character offsets that locate each PII entity in the input text\. The output also includes confidence scores and PII entity types\.
+ `LanguageCode` – Set this parameter to `en`\. Amazon Comprehend supports PII detection in only English text\.

## Redact PII Entities<a name="how-pii-redact"></a>

To redact the PII entities in your text, you must run an asynchronous batch job\. To run the job, upload your documents to Amazon S3, and submit a [StartPiiEntitiesDetectionJob](API_StartPiiEntitiesDetectionJob.md) request\. In your request, include the following required parameters:
+ `InputDataConfig` – Provide an [InputDataConfig](API_InputDataConfig.md) definition for your request, which includes the input properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location of your input documents\.
+ `OutputDataConfig` – Provide an [OutputDataConfig](API_OutputDataConfig.md) definition for your request, which includes the output properties for the job\. For the `S3Uri` parameter, specify the Amazon S3 location where Amazon Comprehend writes the results of its analysis\.
+ `DataAccessRoleArn` – Provide the Amazon Resource Name \(ARN\) of an AWS Identity and Access Management role\. This role must grant Amazon Comprehend read access to your input data and write access to your output location in Amazon S3\. For more information, see [Role\-Based Permissions Required for Asynchronous Operations](access-control-managing-permissions.md#auth-role-permissions)\.
+ `Mode` – Set this parameter to `ONLY_REDACTION`\. With this setting, Amazon Comprehend writes a copy of your input documents to the output location in Amazon S3\. In this copy, each PII entity is redacted\.
+ `RedactionConfig` – Provide a [RedactionConfig](API_RedactionConfig.md) definition for your request, which includes the configuration parameters for the redaction\. Specify the types of PII to redact, and specify whether each PII entity is replaced with the name of its type or a character of your choice:
  + To replace each PII entity with its type, set the `MaskMode` parameter to `REPLACE_WITH_PII_ENTITY_TYPE`\. For example, with this setting, the PII entity "Jane Doe" is replaced with "\[NAME\]"\.
  + To replace the characters in each PII entity with a character of your choice, set the `MaskMode` parameter to `MASK`, and set the `MaskCharacter` parameter to the replacement character\. Provide only a single character\. Valid characters are \!, \#, $, %, &, \*, and @\. For example, with this setting, the PII entity "Jane Doe" can be replaced with "\*\*\*\* \*\*\*"
+ `LanguageCode` – Set this parameter to `en`\. Amazon Comprehend supports PII detection in only English text\.