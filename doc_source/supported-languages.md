# Languages Supported in Amazon Comprehend<a name="supported-languages"></a>

Amazon Comprehend supports a wide variety of languages for its various features\. The languages supported and the features that support them can be seen in the following tables\.

**Topics**
+ [Supported Languages](#supported-languages-1)
+ [Languages Supported by Amazon Comprehend Features](#supported-languages-feature)

## Supported Languages<a name="supported-languages-1"></a>

Amazon Comprehend \(except the **Detect Dominant Language** feature\) supports the following languages for one or more features\. 


| Code | Language | 
| --- | --- | 
| de | German | 
| en | English | 
| es | Spanish | 
| it | Italian  | 
| pt | Portuguese | 
| fr | French | 
| ja | Japanese | 
| ko | Korean | 
| hi | Hindi | 
| ar | Arabic | 
| zh | Chinese \(simplified\) | 
| zh\-TW | Chinese \(traditional\) | 

**Note**  
Amazon Comprehend identifies the language using identifiers from RFC 5646 — if there is a 2\-letter ISO 639\-1 identifier, with a regional subtag if necessary, it uses that\. Otherwise, it uses the ISO 639\-2 3\-letter code\. For more information about RFC 5646, see the *IETF Tools* web site\.



## Languages Supported by Amazon Comprehend Features<a name="supported-languages-feature"></a>


| Feature | Supported Languages | 
| --- | --- | 
|  [Detect the Dominant Language](how-languages.md)  |  See [Detect the Dominant Language](how-languages.md)\.  | 
|  [Detect Entities](how-entities.md)  |  All supported languages\.  | 
|  [Detect Key Phrases](how-key-phrases.md)  |  All supported languages\.  | 
|  [Detect Personally Identifiable Information \(PII\)](how-pii.md)  |  English  | 
|  [Label Documents with Personally Identifiable Information \(PII\)](how-pii-labels.md)  | English | 
|  [Determine Sentiment](how-sentiment.md)  |  All supported languages\.  | 
|  [Analyze Syntax](how-syntax.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\.   | 
|  [Topic Modeling](topic-modeling.md)  |  Not dependent on the language used\.  | 
|  [Custom Classification](how-document-classification.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\.  | 
|  [Custom Entity Recognition](custom-entity-recognition.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\.  | 