# Key phrases<a name="how-key-phrases"></a>

A *key phrase* is a string containing a noun phrase that describes a particular thing\. It generally consists of a noun and the modifiers that distinguish it\. For example, "day" is a noun; "a beautiful day" is a noun phrase that includes an article \("a"\) and an adjective \("beautiful"\)\. Each key phrase includes a score that indicates the level of confidence that Amazon Comprehend has that the string is a noun phrase\. You can use the score to determine if the detection has high enough confidence for your application\.

Detect key phrases operations can be performed using any of the primary languages supported by Amazon Comprehend\. All documents must be in the same language\.

You can use any of the following operations to detect key phrases in a document or set of documents\.
+ [DetectKeyPhrases](API_DetectKeyPhrases.md)
+ [BatchDetectKeyPhrases](API_BatchDetectKeyPhrases.md)
+ [StartKeyPhrasesDetectionJob](API_StartKeyPhrasesDetectionJob.md)

The operations return a list of [KeyPhrase](API_KeyPhrase.md) objects, one for each key phrase in the document\. The `BatchDetectKeyPhrases` operation returns a list of `KeyPhrase` objects, one for each document in the batch\. The `StartKeyPhrasesDetectionJob` operation starts an asynchronous job that produces a file containing a list of `KeyPhrase` objects for each document in the job\.

The following example is the response from the `DetectKeyPhrases` operation\.

```
{
    "LanguageCode": "en",
    "KeyPhrases": [
        {
            "Text": "today",
            "Score": 0.89,
            "BeginOffset": 14,
            "EndOffset": 19
        },
        {
            "Text": "Seattle",
            "Score": 0.91,
            "BeginOffset": 23,
            "EndOffset": 30
        }
    ]
}
```