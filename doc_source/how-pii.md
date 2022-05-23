# Detecting PII entities<a name="how-pii"></a>

You can use Amazon Comprehend to detect *PII entities* in English text documents\. A PII entity is a specific type of personally identifiable information \(PII\)\. Use PII detection to locate the PII entities or redact the PII entities in the text\.

**Topics**
+ [Locate PII entities](#how-pii-locate)
+ [Redact PII entities](#how-pii-redact)
+ [PII universal entity types](#how-pii-types)
+ [Country\-specific PII entity types](#how-pii-types-country)

## Locate PII entities<a name="how-pii-locate"></a>

To locate the PII entities in your text, you can quickly analyze a single document using real\-time analysis\.You also can start an asynchronous batch job on a collection of documents\. 

You can use the console or the API for real\-time analysis of a single document\. Your input text can include up to 5,000 bytes of UTF\-8 encoded characters\.

For example, you can submit the following input text to locate the PII entities:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

The output includes the information that "Paul Santos" has the type `NAME`, "1111\-0000\-1111\-0000" has the type `CREDIT_DEBIT_NUMBER`, and "123 Any Street, Seattle, WA 98109" has the type `ADDRESS`\.

 Amazon Comprehend returns a list of detected PII entities, with the following information for each PII entity:
+ A score that estimates the probability that the detected text span is the detected entity type\.
+ The PII entity type\.
+ The location of the PII entity in the document, specified as character offsets for the start and the end of the entity\.

 For example, the input text mentioned previously produces the following response:

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

## Redact PII entities<a name="how-pii-redact"></a>

To redact the PII entities in your text, you can use the console or the API to start an asynchronous batch job\. Amazon Comprehend returns a copy of the input text with redactions for each PII entity\.

For example, you can submit the following input text to redact the PII entities:

*Hello Paulo Santos\. The latest statement for your credit card account 1111\-0000\-1111\-0000 was mailed to 123 Any Street, Seattle, WA 98109\.*

The output file includes the following text: 

*Hello \*\*\*\*\* \*\*\*\*\*\*\. The latest statement for your credit card account \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* was mailed to \*\*\* \*\*\* \*\*\*\*\*\*\* \*\*\*\*\*\*\*\* \*\* \*\*\*\*\*\.*

## PII universal entity types<a name="how-pii-types"></a>

Some PII entity types are universal \(not specific to individual countries\), such as email addresses and credit card numbers\. Amazon Comprehend detects the following types of universal PII entities:

**ADDRESS**  
A physical address, such as "100 Main Street, Anytown, USA" or "Suite \#12, Building 123"\. An address can include information such as the street, building, location, city, state, country, county, zip code, precinct, and neighborhood\.

**AGE**  
An individual's age, including the quantity and unit of time\. For example, in the phrase "I am 40 years old," Amazon Comprehend recognizes "40 years" as an age\. 

**AWS\_ACCESS\_KEY**  
A unique identifier that's associated with a secret access key; you use the access key ID and secret access key to sign programmatic AWS requests cryptographically\.

**AWS\_SECRET\_KEY**  
A unique identifier that's associated with an access key\. You use the access key ID and secret access key to sign programmatic AWS requests cryptographically\.

**CREDIT\_DEBIT\_CVV**  
A three\-digit card verification code \(CVV\) that is present on VISA, MasterCard, and Discover credit and debit cards\. For American Express credit or debit cards, the CVV is a four\-digit numeric code\.

**CREDIT\_DEBIT\_EXPIRY**  
The expiration date for a credit or debit card\. This number is usually four digits long and is often formatted as month/year or MM/YY\. Amazon Comprehend recognizes expiration dates such as 01/21, 01/2021, and Jan 2021\. 

**CREDIT\_DEBIT\_NUMBER**  
The number for a credit or debit card\. These numbers can vary from 13 to 16 digits in length\. However, Amazon Comprehend also recognizes credit or debit card numbers when only the last four digits are present\. 

**DATE\_TIME**  
A date can include a year, month, day, day of week, or time of day\. For example, Amazon Comprehend recognizes "January 19, 2020" or "11 am" as dates\. Amazon Comprehend will recognize partial dates, date ranges, and date intervals\. It will also recognize decades, such as "the 1990s"\.

**DRIVER\_ID**  
The number assigned to a driver's license, which is an official document permitting an individual to operate one or more motorized vehicles on a public road\. A driver's license number consists of alphanumeric characters\. 

**EMAIL**  
An email address, such as marymajor@email\.com\.

**INTERNATIONAL\_BANK\_ACCOUNT\_NUMBER**  
An International Bank Account Number has specific formats in each country\. See [www\.iban\.com/structure](https://www.iban.com/structure)\.

**IP\_ADDRESS**  
An IPv4 address, such as 198\.51\.100\.0\.

**LICENSE\_PLATE**  
A license plate for a vehicle is issued by the state or country where the vehicle is registered\. The format for passenger vehicles is typically five to eight digits, consisting of upper\-case letters and numbers\. The format varies depending on the location of the issuing state or country\.

**MAC\_ADDRESS**  
A media access control \(MAC\) address is a unique identifier assigned to a network interface controller \(NIC\)\. 

**NAME**  
An individual's name\. This entity type does not include titles, such as Dr\., Mr\., Mrs\., or Miss\. Amazon Comprehend does not apply this entity type to names that are part of organizations or addresses\. For example, Amazon Comprehend recognizes the "John Doe Organization" as an organization, and it recognizes "Jane Doe Street" as an address\. 

**PASSWORD**  
An alphanumeric string that is used as a password, such as "\*very20special\#pass\*"\.

**PHONE**  
A phone number\. This entity type also includes fax and pager numbers\.

**PIN**  
A four\-digit personal identification number \(PIN\) with which you can access your bank account\.

**SWIFT\_CODE**  
A SWIFT code is a standard format of Bank Identifier Code \(BIC\) used to specify a particular bank or branch\. Banks use these codes for money transfers such as international wire transfers\.  
SWIFT codes consist of eight or 11 characters\. The 11\-digit codes refer to specific branches, while eight\-digit codes \(or 11\-digit codes ending in 'XXX'\) refer to the head or primary office\. 

**URL**  
A web address, such as www\.example\.com\.

**USERNAME**  
A user name that identifies an account, such as a login name, screen name, nick name, or handle\.

**VEHICLE\_IDENTIFICATION\_NUMBER**  
A Vehicle Identification Number \(VIN\) uniquely identifies a vehicle\. VIN content and format are defined in the ISO 3779 specification\. Each country has specific codes and formats for VINs\.

## Country\-specific PII entity types<a name="how-pii-types-country"></a>

Some PII entity types are country\-specific, such as passport numbers and other government\-issued ID numbers\. Amazon Comprehend detects the following types of country\-specific PII entities:

**CA\_HEALTH\_NUMBER**  
A Canadian Health Service Number is a 10\-digit unique identifier, required for individuals to access healthcare benefits\.

**CA\_SOCIAL\_INSURANCE\_NUMBER**  
A Canadian Social Insurance Number \(SIN\) is a nine\-digit unique identifier, required for individuals to access government programs and benefits\.   
The SIN is formatted as three groups of three digits, such as 123\-456\-789\. A SIN can be validated through a simple check\-digit process called the [Luhn algorithm](https://www.wikipedia.org/wiki/Luhn_algorithm)\.

**IN\_AADHAAR**  
An Indian Aadhaar is a 12\-digit unique identification number issued by the Indian government to the residents of India\. The Aadhaar format has a space or hyphen after the fourth and eighth digit\.

**IN\_NREGA**  
An Indian National Rural Employment Guarantee Act \(NREGA\) number consists of two letters followed by 14 numbers\.

**IN\_PERMANENT\_ACCOUNT\_NUMBER**  
An Indian Permanent Account Number is a 10\-digit unique alphanumeric number issued by the Income Tax Department\.

**IN\_VOTER\_NUMBER**  
An Indian Voter ID consists of three letters followed by seven numbers\.

**UK\_NATIONAL\_HEALTH\_SERVICE\_NUMBER**  
A UK National Health Service Number is a 10\-17 digit number, such as **485 777 3456**\. The current system formats the 10\-digit number with spaces after the third and sixth digits\. The final digit is an error\-detecting checksum\.   
The 17\-digit number format has spaces after the 10th and 13th digits\.

**UK\_NATIONAL\_INSURANCE\_NUMBER**  
A UK National Insurance Number \(NINO\) provides individuals with access to National Insurance \(social security\) benefits\. It is also used for some purposes in the UK tax system\.   
The number is nine digits long and starts with two letters, followed by six numbers and one letter\. A NINO can be formatted with a space or a dash after the two letters and after the second, forth, and sixth digits\.

**UK\_UNIQUE\_TAXPAYER\_REFERENCE\_NUMBER**  
A UK Unique Taxpayer Reference \(UTR\) is a 10\-digit number that identifies a taxpayer or a business\.

**BANK\_ACCOUNT\_NUMBER**  
A US bank account number, which is typically 10 to 12 digits long\. Amazon Comprehend also recognizes bank account numbers when only the last four digits are present\.

**BANK\_ROUTING**  
A US bank account routing number\. These are typically nine digits long, but Amazon Comprehend also recognizes routing numbers when only the last four digits are present\.

**PASSPORT\_NUMBER**  
A US passport number\. Passport numbers range from six to nine alphanumeric characters\.

**US\_INDIVIDUAL\_TAX\_IDENTIFICATION\_NUMBER**  
A US Individual Taxpayer Identification Number \(ITIN\) is a nine\-digit number that starts with a "9" and contain a "7" or "8" as the fourth digit\. An ITIN can be formatted with a space or a dash after the third and forth digits\.

**SSN**  
A US Social Security Number \(SSN\) is a nine\-digit number that is issued to US citizens, permanent residents, and temporary working residents\. Amazon Comprehend also recognizes Social Security Numbers when only the last four digits are present\.