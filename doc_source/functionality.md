# Text Analysis APIs<a name="functionality"></a>

Amazon Comprehend enables you to examine your documents to gain various insights about their content using a number of pre\-trained models\. 

With Amazon Comprehend, you can perform the following on your documents:
+ [Detect Entities](how-entities.md)—Detect textual references to the names of people, places, and items as well as references to dates and quantities\.
+ [Detect Events](how-events.md)—Analyze documents to detect specific types of events\.
+ [Detect Key Phrases](how-key-phrases.md)—Find key phrases such as "good morning" in a document or set of documents\.
+ [Detect the Dominant Language](how-languages.md)—Examine text to determine the dominant language\.
+ [Detect Personally Identifiable Information \(PII\)](how-pii.md) — Analyze documents to detect personal data that could be used to identify an individual, such as an address, bank account number, or phone number\.
+ [Label Documents with Personally Identifiable Information \(PII\)](how-pii-labels.md) — Label text documents with personally identifiable information \(PII\)\.
+ [Determine Sentiment](how-sentiment.md)—Analyze documents and determine the dominant sentiment of the text\.
+ [Analyze Targeted Sentiment](how-targeted-sentiment.md)—Analyze documents to determine the sentiment associated with specific entities mentioned in the text\.
+ [Analyze Syntax](how-syntax.md)—Parse the words in your text and show the speech syntax for each word and enable you to understand the content of the document\.
+ [Topic Modeling](topic-modeling.md)—Search the content of documents to determine common themes and topics\.

Documents can be processed through these features in several ways: singly or in groups of up to 25 documents run synchronously with the result returned immediately, or in a larger batch run asynchronously, with the result saved to an S3 bucket\. For more information, see [Document Processing Modes](process.md)\.