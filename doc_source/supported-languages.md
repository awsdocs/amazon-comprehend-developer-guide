# Languages supported in Amazon Comprehend<a name="supported-languages"></a>

Amazon Comprehend supports a wide variety of languages for its various features\. The languages supported and the features that support them can be seen in the following tables\.

**Topics**
+ [Supported languages](#supported-languages-1)
+ [Languages supported by Amazon Comprehend features](#supported-languages-feature)

## Supported languages<a name="supported-languages-1"></a>

Amazon Comprehend \(except the **detect dominant language** feature\) supports the following languages for one or more features\. 


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



## Languages supported by Amazon Comprehend features<a name="supported-languages-feature"></a>


| Feature | Supported languages | 
| --- | --- | 
|  [Dominant language](how-languages.md)  |  See [Dominant language](how-languages.md)\.  | 
|  [Entities](how-entities.md)  |  All supported languages\.  | 
|  [Key phrases](how-key-phrases.md)  |  All supported languages\.  | 
|  [Detecting PII entities](how-pii.md)  |  English\.  | 
|  [Labeling PII entities](how-pii-labels.md)  | English\. | 
|  [Sentiment](how-sentiment.md)  |  All supported languages\.  | 
|  [Targeted sentiment](how-targeted-sentiment.md)  |  English\.  | 
|  [Syntax analysis](how-syntax.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\.   | 
|  [Topic modeling](topic-modeling.md)  |  Not dependent on the language used\. Does not support character\-based languages such as Chinese, Japanese, and Korean\.  | 
|  [Custom classification](how-document-classification.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\.  | 
|  [Custom entity recognition](custom-entity-recognition.md)  |  German \(de\), English \(en\), Spanish \(es\), French \(fr\), Italian \(it\), and Portuguese \(pt\)\. Custom Entity Recognition for PDF and Word supports English documents only\.  | 