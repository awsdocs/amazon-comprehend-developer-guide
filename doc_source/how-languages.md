# Detect the Dominant Language<a name="how-languages"></a>

You can use Amazon Comprehend to examine text to determine the dominant language\. Amazon Comprehend identifies the language using identifiers from RFC 5646 — if there is a 2\-letter ISO 639\-1 identifier, with a regional subtag if necessary, it uses that\. Otherwise, it uses the ISO 639\-2 3\-letter code\. For more information about RFC 5646, see [Tags for Identifying Languages](https://tools.ietf.org/html/rfc5646) on the *IETF Tools* web site\.

The response includes a score that indicates the confidence level that Amazon Comprehend has that a particular language is the dominant language in the document\. Each score is independent of the other scores — it does not indicate that a language makes up a particular percentage of a document\.

If a long document, like a book, is written in multiple languages, you can break the long document into smaller pieces and run the `DetectDominantLanguage` operation on the individual pieces\. You can then aggregate the results to determine the percentage of each language in the longer document\.

Amazon Comprehend can detect the following languages\.


| Code | Language | Code | Language | Code | Language | 
| --- | --- | --- | --- | --- | --- | 
| af | Afrikaans | hy | Armenian | ps | Pushto | 
| am | Amharic | ilo | Iloko | qu | Quechua | 
| ar | Arabic | id | Indonesian | ro | Romanian | 
| as | Assamese | is | Icelandic | ru | Russian | 
| az | Azerbaijani | it | Italian | sa | Sanskrit | 
| ba | Bashkir | jv | Javanese | si | Sinhala | 
| be | Belarusian | ja | Japanese | sk | Slovak | 
| bn | Bengali | kn | Kannada | sl | Slovenian | 
| bs | Bosnian | ka | Georgian | sd | Sindhi | 
| bg | Bulgarian | kk | Kazakh | so | Somali | 
| ca | Catalan | km | Central Khmer | es | Spanish | 
| ceb | Cebuano | ky | Kirghiz | sq | Albanian | 
| cs | Czech | ko | Korean | sr | Serbian | 
| cv | Chuvash | ku | Kurdish | su | Sundanese | 
| cy | Welsh | la | Latin | sw | Swahili | 
| da | Danish | lv | Latvian | sv | Swedish | 
| de | German | lt | Lithuanian | ta | Tamil | 
| el | Greek | lb | Luxembourgish | tt | Tatar | 
| en | English | ml | Malayalam | te | Telugu | 
| eo | Esperanto | mr | Marathi | tg | Tajik | 
| et | Estonian | mk | Macedonian | tl | Tagalog | 
| eu | Basque | mg | Malagasy | th | Thai | 
| fa | Persian | mn | Mongolian | tk | Turkmen | 
| fi | Finnish | ms | Malay | tr | Turkish | 
| fr | French | my | Burmese | ug | Uighur | 
| gd | Scottish Gaelic | ne | Nepali | uk | Ukrainian | 
| ga | Irish | new | Newari | ur | Urdu | 
| gl | Galician | nl | Dutch | uz | Uzbek | 
| gu | Gujarati | no | Norwegian | vi | Vietnamese | 
| ht | Haitian | or | Oriya | yi | Yiddish | 
| he | Hebrew | pa | Punjabi | yo | Yoruba | 
| hi | Hindi | pl | Polish | zh | Chinese \(Simplified\) | 
| hr | Croatian | pt | Portuguese | zh\-TW | Chinese \(Traditional\) | 
| hu | Hungarian |   |   |   |   | 

You can use any of the following operations to detect the dominant language in a document or set of documents\.
+ [DetectDominantLanguage](API_DetectDominantLanguage.md)
+ [BatchDetectDominantLanguage](API_BatchDetectDominantLanguage.md)
+ [StartDominantLanguageDetectionJob](API_StartDominantLanguageDetectionJob.md)

The `DetectDominantLanguage` operation returns a [DominantLanguage](API_DominantLanguage.md) object\. The `BatchDetectDominantLanguage` operation returns a list of `DominantLanguage` objects, one for each document in the batch\. The `StartDominantLanguageDetectionJob` operation starts an asynchronous job that produces a file containing a list of `DominantLanguage` objects, one for each document in the job\.

The following example is the response from the `DetectDominantLanguage` operation\.

```
{
    "Languages": [
        {
            "LanguageCode": "en",
            "Score": 0.9793661236763
        }
    ]
}
```