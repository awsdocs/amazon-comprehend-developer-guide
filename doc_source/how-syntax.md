# Syntax analysis<a name="how-syntax"></a>

Use syntax analysis to parse the words from the document and return the part of speech, or syntactic function, for each word in the document\. You can identify the nouns, verbs, adjectives and so on in your document\. Use this information to gain a richer understanding of the content of your documents, and to understand the relationship of the words in the document\.

For example, you can look for the nouns in a document and then look for the verbs related to those nouns\. In a sentence like "My grandmother moved her couch" you can see the nouns, "grandmother" and "couch," and the verb, "moved\." You can use this information to build applications for analyzing text for word combinations that you are interested in\.

To start the analysis, Amazon Comprehend parses the source text to find the individual words in the text\. After the text is parsed, each word is assigned the part of speech that it takes in the source text\.

Amazon Comprehend can identify 17 parts of speech\. The parts of speech recognized are:


| Token | Part of speech | 
| --- | --- | 
| ADJ | Adjective Words that typically modify nouns\. | 
| ADP | Adposition The head of a prepositional or postpositional phrase\. | 
| ADV | Adverb Words that typically modify verbs\. They may also modify adjectives and other adverbs\. | 
| AUX | Auxiliary Function words that accompanies the verb of a verb phrase\. | 
| CCONJ | Coordinating conjunction Words that links words or phrases without subordinating one to the other\. | 
| DET | Determiner Articles and other words that specify a particular noun phrase\. | 
| INTJ | Interjection Words used as an exclamation or part of an exclamation\. | 
| NOUN | Noun Words that specify a person, place, thing, animal, or idea\. | 
| NUM | Numeral Words, typically determiners, adjectives, or pronouns, that express a number\. | 
| O | Other Words that can't be assigned a part of speech category\. | 
| PART | Particle Function words associated with another word or phrase to impart meaning\.  | 
| PRON | Pronoun Words that substitute for nouns or noun phrases\. | 
| PROPN | Proper nounA noun that is the name of a specific individual, place or object\. | 
| PUNCT | Punctuation Non\-alphabetical characters that delimit text\. | 
| SCONJ | Subordinating conjunction A conjunction that links parts of sentences by make one of them part of the other\. | 
| SYM | SymbolWord\-like entities such as the dollar sign \($\) or mathematical symbols\. | 
| VERB | VerbWords that signal events and actions\. | 

For more information about the parts of speech, see [Universal POS tags](http://universaldependencies.org/u/pos/) at the *Universal Dependencies* website\.

The operations return tokens that identify the word and the part of speech that the word represents in the text\. Each token represents a word in the source text\. It provides the location of the word in the source, the part of speech that the word takes in the text, the confidence that Amazon Comprehend has that the part of speech was correctly identified, and the word that was parsed from the source text\.

The following is the structure of the list of syntax tokens\. One syntax token is generated for each word in the document\. 

```
{
   "SyntaxTokens": [ 
      { 
         "BeginOffset": number,
         "EndOffset": number,
         "PartOfSpeech": { 
            "Score": number,
            "Tag": "string"
         },
         "Text": "string",
         "TokenId": number
      }
   ]
}
```

Each token provides the following information:
+ `BeginOffset` and `EndOffset`—Provides the location of the word in the input text\. 
+ `PartOfSpeech`—Provides two pieces of information, the `Tag` that identifies the part of speech and the `Score` that represents the confidence that Amazon Comprehend Syntax has that the part of speech was correctly identifies\.
+ `Text`—Provides the word that was identified\.
+ `TokenId`—Provides an identifier for the token\. The identifier is the position of the token in the list of tokens\.