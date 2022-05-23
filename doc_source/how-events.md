# Events<a name="how-events"></a>

## <a name="events-result-schema"></a>

Use *event detection* to analyze text documents for speciﬁc types of events and their related entities\. Amazon Comprehend supports event detection across large collections of documents using asynchronous analysis jobs\. For more information about events, including example event analysis jobs, see [ Announcing the launch of Amazon Comprehend Events ](http://aws.amazon.com/blogs/machine-learning/announcing-the-launch-of-amazon-comprehend-events/)

### Entities<a name="how-events-entities"></a>

From the input text, Amazon Comprehend extracts a list of entities that are related to the detected event\. An *entity* can be a real\-world object, such as a person, place, or location; an entity can also be a concept, such as a measurement, date, or quantity\. Each occurrence of an entity is identified by a *mention*, which is a textual reference to the entity in the input text\. For each unique entity, all mentions are grouped into a list\. This list provides details for each location in the input text where the entity occurs\. Amazon Comprehend detects only the entities associated with supported event types\.

Each entity associated with a supported event type returns with the following related details:
+ **Mentions**: Details for each occurrence of the same entity in the input text\.
  + **BeginOffset**: A character offset in the input text that shows where the mention begins \(the first character is at position 0\)\. 
  + **EndOffset**: A character offset in the input text that shows where the mention ends\.
  + **Score**: The level of confidence that Amazon Comprehend has in the accuracy of the entity's type\.
  + **GroupScore**: The level of confidence from Amazon Comprehend that the mention is correctly grouped with other mentions of the same entity\.
  + **Text**: The text of the entity\.
  + **Type**: The entity's type\. For all supported entity types, see [Entity types](#events-entity-types)\.

### Events<a name="how-events-output"></a>

Amazon Comprehend returns the list of events \(of supported event types\) that it detects in the input text\. Each event returns with the following related details:
+ **Type**: The event's type\. For all supported event types, see [Event types](#events-types)\.
+ **Arguments**: A list of arguments that are related to the detected event\. An *argument* consists of an entity that is related to the detected event\. The argument's role describes the relationship, such as *who* did *what*, *where *and *when*\.
  + **EntityIndex**: An index value that identifies an entity from the list of entities that Amazon Comprehend returned for this analysis\.
  + **Role**: The argument type, which describes how the entity for this argument is related to the event\. For all supported argument types, see [Argument types](#events-argument-types)\.
  + **Score**: The level of confidence that Amazon Comprehend has in the accuracy of the role detection\.
+ **Triggers**: A list of triggers for the detected event\. A *trigger* is a single word or phrase that indicates the occurrence of the event\.
  + **BeginOffset**: A character offset in the input text that shows where the trigger begins \(the first character is at position 0\)\.
  + **EndOffset**: A character offset in the input text that shows where the trigger ends\.
  + **Score**: The level of confidence that Amazon Comprehend has in the accuracy of the detection\.
  + **Text**: The text of the trigger\.
  + **GroupScore**: The level of confidence from Amazon Comprehend that the trigger is correctly grouped with other triggers for the same event\.
  + **Type**: The type of event that this trigger indicates\.

## Detect events results format<a name="how-events-results"></a>

When your event detection job completes, Amazon Comprehend writes the analysis results to the Amazon S3 output location that you specified when you started the job\.

For each detected event, the output provides details in the following format:

```
{
   "Entities": [
     {
       "Mentions": [
         {
           "BeginOffset": number,
           "EndOffset": number,
           "Score": number,
           "GroupScore": number,
           "Text": "string",
           "Type": "string"
         }, ...
       ]    
     }, ...
   ],
   "Events": [
     {
       "Type": "string",
       "Arguments": [
         {                   
           "EntityIndex": number,   
           "Role": "string",
           "Score": number
         }, ...
       ],
       "Triggers": [
         {
           "BeginOffset": number,
           "EndOffset": number,
           "Score": number,
           "Text": "string",
           "GroupScore": number,
           "Type": "string"
         }, ...
       ]
     }, ...
   ]
 }
```

## Supported types for entities, events, and arguments<a name="events-reference-types"></a>

### Entity types<a name="events-entity-types"></a>


| Type | Description | 
| --- | --- | 
| DATE | Any reference to a date or time, whether specific or general\. | 
| FACILITY | Buildings, airports, highways, bridges, and other permanent man\-made structures and real estate improvements\. | 
| LOCATION | Physical locations such as streets, cities, states, countries, bodies of water, or geographic coordinates\. | 
| MONETARY\_VALUE | The value of something in US or other currency\. The value can be specific or approximate\. | 
| ORGANIZATION | Companies and other groups of people defined by an established organizational structure\. | 
| PERSON | The names or nicknames of individuals or fictional characters\. | 
| PERSON\_TITLE | Any title which describes a person, which is usually an employment category \(such as CEO\) or honorific \(such as Mr\.\)\. | 
| QUANTITY | A number or value and the unit of measurement\. | 
| STOCK\_CODE | A stock ticker symbol, such as AMZN, an International Securities Identification Number \(ISIN\), Committee on Uniform Securities Identification Procedures \(CUSIP\), or Stock Exchange Daily Official List \(SEDOL\)\. | 

### Event types<a name="events-types"></a>


| Type | Description | 
| --- | --- | 
| BANKRUPTCY | A legal proceeding involving a person or company unable to repay outstanding debts\. | 
| EMPLOYMENT | Occurs when an employee is hired, fired, retired, or otherwise changes employment state\.  | 
| CORPORATE\_ACQUISTION | Occurs when a company obtains the possession of most or all of another company's shares or physical assets to gain control of that company\. | 
| INVESTMENT\_GENERAL | Occurs when a person or company purchases an asset with the prospect of generating future income or appreciation\. | 
| CORPORATE\_MERGER | Occurs when two or more companies unite to create a new legal entity\.  | 
| IPO | An initial public offering \(IPO\) of shares of a private corporation to the public in a new stock issuance\. | 
| RIGHTS\_ISSUE | A group of rights offered to existing shareholders to purchase additional stock shares, known as subscription warrants, in proportion to their existing holdings\. | 
| SECONDARY\_OFFERING | An offer of securities by a shareholder of a company\.  | 
| SHELF\_OFFERING | A Securities and Exchange Commission \(SEC\) provision that allows an issuer to register a new issue of security and sell portions of the issue over a period of time without re\-registering the security or incurring penalties\. Also known as a shelf registration\. | 
| TENDER\_OFFERING | An offer to purchase some or all of shareholders' shares in a company\. | 
| STOCK\_SPLIT | Occurs when a company's board of directors increases the number of shares that are outstanding by issuing more shares to current shareholders\. This event also applies to reverse stock splits\. | 

### Argument types<a name="events-argument-types"></a>


**Argument types for BANKRUPTCY**  

| Argument type | Description | 
| --- | --- | 
| FILER | The person or company filing the bankruptcy\.  | 
| DATE | The date or time of bankruptcy\. | 
| PLACE | Location or facility where \(or nearest to where\) the bankruptcy took place\. | 


**Argument types for EMPLOYMENT**  

| Type | Description | 
| --- | --- | 
| EMPLOYEE | The person employed by a company\. | 
| EMPLOYEE\_TITLE | The title of the employee\. | 
| EMPLOYER | The person or company employing the employee\. | 
| END\_DATE | The start date or time of the employment\. | 
| START\_DATE | The end date or time of the employment\. | 


**Argument types for CORPORATE\_ACQUISTION, INVESTMENT\_GENERAL**  

| Type | Description | 
| --- | --- | 
| AMOUNT | The monetary value associated with the transaction\. | 
| INVESTEE | The person or company associated with the investment\. | 
| INVESTOR | The person or company investing in the asset\. | 
| DATE | The date or time of the acquisition or investment\. | 
| PLACE | Location where \(or nearest to where\) the acquisition or investment took place\. | 


**Argument types for CORPORATE\_MERGER**  

| Type | Description | 
| --- | --- | 
| DATE | The date or time of the merger\. | 
| NEW\_COMPANY | The new legal entity resulting from the merger\. | 
| PARTICIPANT | The company involved in the merger\. | 


**Argument types for IPO, RIGHTS\_ISSUE, SECONDARY\_OFFERING, SHELF\_OFFERING, TENDER\_OFFERING**  

| Type | Description | 
| --- | --- | 
| EXPIRE\_DATE | The expiration date or time of the offering\. | 
| INVESTOR | The person or company investing in the asset\. | 
| OFFEREE | The person or company receiving the offering\. | 
| OFFERING\_AMOUNT | The monetary value associated with the offering\. | 
| OFFERING\_DATE | The date or time of the offering\. | 
| OFFEROR | The person or company initiating the offering\. | 
| OFFEROR\_TOTAL\_VALUE | The total monetary value associated with the offering\. | 
| RECORD\_DATE | The record date or time of the offering\. | 
| SELLING\_AGENT | The person or company facilitating the sale of the offering\.  | 
| SHARE\_PRICE | The monetary value associated with the share price\. | 
| SHARE\_QUANTITY | The number of shares associated with the offering\. | 
| UNDERWRITERS | The company associated with the underwriting of the offering\. | 


**Argument types for STOCK\_SPLIT**  

| Type | Description | 
| --- | --- | 
| COMPANY | The company issuing shares of the stock split\. | 
| DATE | The date or time of the stock split\. | 
| SPLIT\_RATIO | The ratio of the increased new number of shares outstanding to the current number of shares before the stock split\.  | 