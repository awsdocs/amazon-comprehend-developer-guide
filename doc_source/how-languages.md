# Dominant language<a name="how-languages"></a>

You can use Amazon Comprehend to examine text to determine the dominant language\. Amazon Comprehend identifies the language using identifiers from RFC 5646 — if there is a 2\-letter ISO 639\-1 identifier, with a regional subtag if necessary, it uses that\. Otherwise, it uses the ISO 639\-2 3\-letter code\. For more information about RFC 5646, see [Tags for identifying languages](https://tools.ietf.org/html/rfc5646) on the *IETF Tools* web site\.

The response includes a score that indicates the confidence level that Amazon Comprehend has that a particular language is the dominant language in the document\. Each score is independent of the other scores — it does not indicate that a language makes up a particular percentage of a document\.

If a long document, like a book, is written in multiple languages, you can break the long document into smaller pieces and run the `DetectDominantLanguage` operation on the individual pieces\. You can then aggregate the results to determine the percentage of each language in the longer document\.

Amazon Comprehend can detect the following languages\.


| Code | Language | 
| --- | --- | 
| af | Afrikaans | 
| am | Amharic | 
| ar | Arabic | 
| as | Assamese | 
| az | Azerbaijani | 
| ba | Bashkir | 
| be | Belarusian | 
| bn | Bengali | 
| bs | Bosnian | 
| bg | Bulgarian | 
| ca | Catalan | 
| ceb | Cebuano | 
| cs | Czech | 
| cv | Chuvash | 
| cy | Welsh | 
| da | Danish | 
| de | German | 
| el | Greek | 
| en | English | 
| eo | Esperanto | 
| et | Estonian | 
| eu | Basque | 
| fa | Persian | 
| fi | Finnish | 
| fr | French | 
| gd | Scottish Gaelic | 
| ga | Irish | 
| gl | Galician | 
| gu | Gujarati | 
| ht | Haitian | 
| he | Hebrew | 
| ha | Hausa | 
| hi | Hindi | 
| hr | Croatian | 
| hu | Hungarian | 
| hy | Armenian | 
| ilo | Iloko | 
| id | Indonesian | 
| is | Icelandic | 
| it | Italian | 
| jv | Javanese | 
| ja | Japanese | 
| kn | Kannada | 
| ka | Georgian | 
| kk | Kazakh | 
| km | Central Khmer | 
| ky | Kirghiz | 
| ko | Korean | 
| ku | Kurdish | 
| lo | Lao | 
| la | Latin | 
| lv | Latvian | 
| lt | Lithuanian | 
| lb | Luxembourgish | 
| ml | Malayalam | 
| mt | Maltese | 
| mr | Marathi | 
| mk | Macedonian | 
| mg | Malagasy | 
| mn | Mongolian | 
| ms | Malay | 
| my | Burmese | 
| ne | Nepali | 
| new | Newari | 
| nl | Dutch | 
| no | Norwegian | 
| or | Oriya | 
| om  | Oromo | 
| pa | Punjabi | 
| pl | Polish | 
| pt | Portuguese | 
| ps | Pushto | 
| qu | Quechua | 
| ro | Romanian | 
| ru | Russian | 
| sa | Sanskrit | 
| si | Sinhala | 
| sk | Slovak | 
| sl | Slovenian | 
| sd | Sindhi | 
| so | Somali | 
| es | Spanish | 
| sq | Albanian | 
| sr | Serbian | 
| su | Sundanese | 
| sw | Swahili | 
| sv | Swedish | 
| ta | Tamil | 
| tt | Tatar | 
| te | Telugu | 
| tg | Tajik | 
| tl | Tagalog | 
| th | Thai | 
| tk | Turkmen | 
| tr | Turkish | 
| ug | Uighur | 
| uk | Ukrainian | 
| ur | Urdu | 
| uz | Uzbek | 
| vi | Vietnamese | 
| yi | Yiddish | 
| yo | Yoruba | 
| zh | Chinese \(Simplified\) | 
| zh\-TW | Chinese \(Traditional\) | 

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